---
title: 陣列界限的宣告不可以出現在類型規範中
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: 50e1cd0e41da467a9e816c8e5d64d09a36923d65
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665740"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a>陣列界限的宣告不可以出現在類型規範中
陣列大小不可以宣告的資料類型指定名稱的一部分。  
  
 **錯誤 ID:** BC30638  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 指定陣列緊接在變數的名稱，而不是將陣列大小放在型別之後, 在下列範例所示的大小。  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
- 定義陣列，並將它與所需數目的項目，初始化，如下列範例所示。  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a>另請參閱

- [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
