---
title: 錯誤：非驗證防火牆 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.firewall.noauth
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a72d16869c92b1965fae8db0ae32146a3a57e67
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63399212"
---
# <a name="error-firewall-no-authentication"></a>錯誤：防火牆無任何驗證
遠端機器上的網際網路連線防火牆並未設定允許遠端偵錯。 針對使用 `No Authentication` 的遠端偵錯，msvsmon.exe 必須加入至例外狀況清單。 可能也必須開啟某些 IPSEC 通訊埠。

> [!NOTE]
> 遠端偵錯工具可以自動設定 Windows 防火牆。 當使用 Windows 防火牆以外的防火牆 (例如，協力廠商軟體防火牆或硬體防火牆) 時，必須手動設定防火牆允許遠端偵錯。 若要執行這項操作，請允許 msvsmon.exe 接聽所在的 TCP/IP 通訊埠上的流量。 根據預設，這些通訊埠為 4018 和 4019，其中 4018 會在所有作業系統上使用，而 4019 僅在 Windows x64 上用來允許對 x86 處理序進行偵錯。

 如需詳細資訊，請參閱 <<c0> [ 遠端偵錯](../debugger/remote-debugging.md)。