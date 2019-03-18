---
title: 由於內部錯誤，無法取得完整作業系統名稱
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: 6a0e24743c861ba92fc284a84fa4ef26e2ee48a8
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "58022764"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>由於內部錯誤，無法取得完整作業系統名稱
由於內部錯誤，無法取得完整作業系統名稱。 這可能是因為目前電腦上沒有 WMI 存在所造成。  
  
 呼叫 `My.Computer.Info.OSFullName` 屬性失敗。 如果目前電腦上未安裝 Windows Management Instrumentation (WMI)，就可能會發生這項失敗。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  將包圍呼叫的 `Try...Catch` 區塊加入 `My.Computer.Info.OSFullName` 屬性中。  
  
2.  如需 WMI 及其安裝方式的詳細資訊，請移至，並搜尋"Windows Management Instrumentation Core"。  
  
## <a name="see-also"></a>另請參閱

- [My.Computer.Info.OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [在 .NET 中處理和擲回例外狀況](../../standard/exceptions/index.md)
- [Try...Catch...Finally 陳述式](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
