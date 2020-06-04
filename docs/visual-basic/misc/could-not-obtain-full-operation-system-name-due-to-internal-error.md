---
title: 由於內部錯誤，無法取得完整作業系統名稱
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: 67e8fb5e906800d28bf15714463b7ff6ae585693
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402274"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>由於內部錯誤，無法取得完整作業系統名稱
由於內部錯誤，無法取得完整作業系統名稱。 這可能是因為目前電腦上沒有 WMI 存在所造成。  
  
 呼叫 `My.Computer.Info.OSFullName` 屬性失敗。 如果目前電腦上未安裝 Windows Management Instrumentation (WMI)，就可能會發生這項失敗。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 將包圍呼叫的 `Try...Catch` 區塊加入 `My.Computer.Info.OSFullName` 屬性中。  
  
2. 如需 WMI 及其安裝方式的詳細資訊，請移至並搜尋「Windows Management Instrumentation 核心」。  
  
## <a name="see-also"></a>另請參閱

- [我的 OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [在 .NET 中處理和擲回例外狀況](../../standard/exceptions/index.md)
- [Try...Catch...Finally 陳述式](../language-reference/statements/try-catch-finally-statement.md)
