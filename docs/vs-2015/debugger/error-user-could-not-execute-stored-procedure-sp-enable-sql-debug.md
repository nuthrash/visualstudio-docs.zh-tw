---
title: 錯誤：使用者無法執行預存程序 sp_enable_sql_debug |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_accessdenied
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 11957495-c238-4cc5-8937-e4026f5e10e1
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1f463aca03cd0e869f4028f8e086c623295fd2f6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945511"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>錯誤：使用者無法執行預存程序 sp_enable_sql_debug
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

預存程序 sp_enable_sql_debug 無法在伺服器上執行。 可能的原因如下：  
  
- 連接問題。 您需要穩定的連接到伺服器。  
  
- 沒有必要的伺服器使用權限。 若要在 SQL Server 2005 上進行偵錯，執行 Visual Studio 的帳戶和用來連接至 SQL Server 的帳戶都必須是系統管理員角色的成員。 用來連接至 SQL Server 的帳戶就是您的 Windows 使用者帳戶 (如果您使用 Windows 驗證)，或具有使用者 ID 和密碼的帳戶 (如果您使用 SQL 驗證)。  
  
  如需詳細資訊，請參閱[如何：設定 SQL Server 權限偵錯](http://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)。  
  
## <a name="see-also"></a>另請參閱  
 [如何：設定 SQL Server 權限偵錯](http://msdn.microsoft.com/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [設定 SQL 偵錯](http://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3)
