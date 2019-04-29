---
title: 選擇性參數必須指定預設值
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 01c0abb366e8605a9b153333e645fc3276b6bd16
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772589"
---
# <a name="optional-parameters-must-specify-a-default-value"></a>選擇性參數必須指定預設值
選擇性參數必須提供預設值，如果未提供參數呼叫程序可以使用。  
  
 **錯誤 ID:** BC30812  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 指定選擇性參數，預設的值例如：  
  
    ```  
    Sub Proc1(ByVal X As Integer,   
          Optional ByVal Y As String = "Default Value")  
       MsgBox("Default argument is: " & Y)  
    End Sub  
    ```  
  
## <a name="see-also"></a>另請參閱

- [Optional](../../../visual-basic/language-reference/modifiers/optional.md)
