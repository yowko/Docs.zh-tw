---
title: '&#39;&lt;membername&gt;&#39; 模稜兩可，跨繼承的介面 &#39;&lt;介面名稱 1>.<&gt;&#39; 和 &#39;&lt;介面名稱 2>&gt;&#39;'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0bf4a9c263fd197cdd5d5b4886ee18e2ff112488
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="39ltmembernamegt39-is-ambiguous-across-the-inherited-interfaces-39ltinterfacename1gt39-and-39ltinterfacename2gt39"></a>&#39;&lt;membername&gt;&#39; 模稜兩可，跨繼承的介面 &#39;&lt;介面名稱 1>.<&gt;&#39; 和 &#39;&lt;介面名稱 2>&gt;&#39;
繼承自多個介面具有相同名稱的兩個或多個成員的介面。  
  
 **錯誤 ID:** BC30685  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   將值轉換成您想要使用; 基底介面例如：  
  
    ```  
    Interface Left  
        Sub MySub()  
    End Interface  
  
    Interface Right  
        Sub MySub()  
    End Interface  
  
    Interface LeftRight  
        Inherits Left, Right  
    End Interface  
  
    Module test  
        Sub Main()  
            Dim x As LeftRight  
            ' x.MySub()  'x is ambiguous.  
            CType(x, Left).MySub() ' Cast to base type.  
            CType(x, Right).MySub() ' Call the other base type.  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
