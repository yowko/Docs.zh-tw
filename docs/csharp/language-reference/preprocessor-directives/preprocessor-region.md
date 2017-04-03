---
title: "#區域 (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#region'
dev_langs:
- CSharp
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2924daffcdc44c8f5ba5cf97c5b141c0dd07ca4a
ms.lasthandoff: 03/13/2017

---
# <a name="region-c-reference"></a>#區域 (C# 參考)
`#region` 可讓您指定程式碼區塊，當您使用 Visual Studio 程式碼編輯器的[大綱](https://docs.microsoft.com/visualstudio/ide/outlining)時，可以展開或摺疊該程式碼區塊。 在較長的程式碼檔案中，能夠摺疊或隱藏一或多個區域是很方便的，如此您可以專注於目前處理的檔案部分。 下例示範如何定義區域：  
  
```  
#region MyClass definition  
public class MyClass   
{  
    static void Main()   
    {  
    }  
}  
#endregion  
```  
  
## <a name="remarks"></a>備註  
 `#region` 區塊必須以 [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) 指示詞結束。  
  
 `#region` 區塊不能與 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 區塊重疊。 不過，`#region` 區塊可以巢狀方式置於 `#if` 區塊中，而 `#if` 區塊可以巢狀方式置於 `#region` 區塊中。  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)

