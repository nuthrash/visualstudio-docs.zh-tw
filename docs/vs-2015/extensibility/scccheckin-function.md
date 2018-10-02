---
title: SccCheckin 函式 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 27d2f5fc2bec3f7e082593e3adcd65a0407f0bc2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487703"
---
# <a name="scccheckin-function"></a>SccCheckin 函式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[SccCheckin 函式](https://docs.microsoft.com/visualstudio/extensibility/scccheckin-function)。  
  
此函式會檢查在先前會在簽出原始檔控制系統，儲存所做的變更和建立的新版本的檔案。 此函式呼叫計數與簽入的檔案名稱的陣列。  
  
## <a name="syntax"></a>語法  
  
```cpp#  
SCCRTN SccCheckin (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPSTR*    lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>參數  
 pvContext  
 [in]原始檔控制外掛程式的內容結構。  
  
 hWnd  
 [in]SCC 外掛程式時，可以使用當做父代上，它會提供任何對話方塊 IDE 視窗的控制代碼。  
  
 nFiles  
 [in]選取要簽入的檔案數目。  
  
 lpFileNames  
 [in]要簽入的檔案的完整格式的本機路徑名稱的陣列。  
  
 lpComment  
 [in]要套用至每個選取的檔案簽入註解。 這是`NULL`如果原始檔控制外掛程式應該會提示使用者輸入註解。  
  
 Stored  
 [in]命令的旗標，可能是 0 或`SCC_KEEP_CHECKEDOUT`。  
  
 pvOptions  
 [in]SCC 外掛程式專屬選項。  
  
## <a name="return-value"></a>傳回值  
 此函式的原始檔控制外掛程式實作應該會傳回下列值之一：  
  
|值|描述|  
|-----------|-----------------|  
|SCC_OK|已成功簽入檔案永遠可使用。|  
|SCC_E_FILENOTCONTROLLED|選取的檔案不在原始檔控制之下。|  
|SCC_E_ACCESSFAILURE|發生問題，存取原始檔控制系統，可能是因為網路或競爭問題。 建議使用重試。|  
|SCC_E_NONSPECIFICERROR|不明確的失敗。 檔案未簽入。|  
|SCC_E_NOTCHECKEDOUT|使用者將會有未簽出檔案，因此無法簽入。|  
|SCC_E_CHECKINCONFLICT|無法執行簽入，因為：<br /><br /> -另一位使用者已繼續簽入和`bAutoReconcile`時發生錯誤。<br /><br /> -或-<br /><br /> （例如，當檔案是二進位），則無法執行-自動合併。|  
|SCC_E_VERIFYMERGE|檔案已經自動合併，但有尚未簽入暫止的使用者驗證。|  
|SCC_E_FIXMERGE|檔案已經自動合併，但尚未簽因合併衝突必須以手動方式解決。|  
|SCC_E_NOTAUTHORIZED|若要執行這項作業不允許的使用者。|  
|SCC_I_OPERATIONCANCELED|在完成之前，已取消操作。|  
|SCC_I_RELOADFILE|必須重新載入檔案或專案。|  
|SCC_E_FILENOTEXIST|找不到本機檔案。|  
  
## <a name="remarks"></a>備註  
 註解適用於所簽入的所有檔案。 註解引數可以是`null`字串，在此情況下的原始檔控制外掛程式可以提示使用者輸入的每個檔案的註解字串。  
  
 `fOptions`引數可以指定值為`SCC_KEEP_CHECKEDOUT`旗標，表示簽入的檔案，並再次查看使用者的意圖。  
  
## <a name="see-also"></a>另請參閱  
 [原始檔控制外掛程式 API 函式](../extensibility/source-control-plug-in-api-functions.md)
