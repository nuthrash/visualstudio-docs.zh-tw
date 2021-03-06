---
title: 需要 Proxy 授權 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 74f8fdd738c613977a73cc3d79b5ba880c7e6e74
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116091"
---
# <a name="proxy-authorization-required"></a>所需的 Proxy 授權
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

通常當使用者透過 Proxy 伺服器連接到 Visual Studio Online，而 Proxy 伺服器封鎖呼叫時，就會發生這個錯誤。 Visual Studio Online 可用來讓使用者保持登入至 IDE。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 重新啟動 Visual Studio。 應該會出現 [Proxy 驗證] 對話方塊。 在對話方塊中輸入您的認證。  
  
- 如果上述步驟無法解決問題，這可能是因為您的 Proxy 伺服器沒有提示輸入 http://go.microsoft.com 位址的認證，而是提示輸入 *.visualStudio.com 位址的認證。 對於這些伺服器，您必須將下列清單列為允許清單，以解除封鎖 Visual Studio 中的所有登入情節：  
  
    - * windows.net  
  
    - *.microsoftonline.com  
  
    - *.visualstudio.com  
  
    - *.microsoft.com  
  
    - *.live.com  
  
- 否則您可以移除 http://go.microsoft.com位址從允許清單，以便 proxy 驗證對話方塊會顯示兩個 http://go.microsoft.com位址及伺服器端點時重新啟動 Visual Studio。  
  
- OR  
  
- 如果您想要將您的預設認證用於 Proxy，您可以執行下列作業：  
  
    1. 在 **%ProgramFiles%\Microsoft Visual Studio 14.0\Common7\IDE** (或 **%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Common7\IDE**) 尋找 devenv.exe.config (devenv.exe 組態檔)。  
  
    2. 在組態檔中，找出 `<system.net>` 區塊，並加入下列程式碼：  
  
        ```xml  
        <defaultProxy enabled="true" useDefaultCredentials="true">  
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>  
        </defaultProxy>  
  
        ```  
  
         您必須在 `proxyaddress="<http://<yourproxy:port#>`中插入您的網路的正確 Proxy 位址。  
  
- OR  
  
- 您也可以遵循 [這篇文章](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) 中的指令，加入允許您使用 Proxy 的程式碼。
