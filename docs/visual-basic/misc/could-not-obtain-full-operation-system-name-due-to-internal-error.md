---
title: 由於內部錯誤，無法取得完整作業系統名稱
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: f85ca5f7f325cb0dd2b8fc55d3f90f6abdfd4a7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33635073"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>由於內部錯誤，無法取得完整作業系統名稱
由於內部錯誤，無法取得完整作業系統名稱。 這可能是因為目前電腦上沒有 WMI 存在所造成。  
  
 呼叫 `My.Computer.Info.OSFullName` 屬性失敗。 如果目前電腦上未安裝 Windows Management Instrumentation (WMI)，就可能會發生這項失敗。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  將包圍呼叫的 `Try...Catch` 區塊加入 `My.Computer.Info.OSFullName` 屬性中。  
  
2.  如需 WMI 及其安裝它的詳細資訊，請移至，並搜尋"Windows Management Instrumentation Core"。  
  
## <a name="see-also"></a>另請參閱  
 [My.Computer.Info.OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)  
 [例外狀況和 Visual Basic 中的錯誤處理](http://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)  
 [Try...Catch...Finally 陳述式](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
