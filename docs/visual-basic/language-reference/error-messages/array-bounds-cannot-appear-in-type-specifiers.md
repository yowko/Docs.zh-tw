---
title: 陣列界限的宣告不可以出現在類型規範中
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: 45787db51de562f2266c587fd2bb15ef29ebefbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>陣列界限的宣告不可以出現在類型規範中
陣列大小不可以宣告做為資料類型規範的一部分。  
  
 **錯誤 ID:** BC30638  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   指定緊接在型別之後，而陣列大小的變數名稱在下列範例所示陣列的大小。  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   定義陣列，並初始化與所需數目的項目，如下列範例所示。  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
