---
description: '##region - C# 參考'
title: '##region - C# 參考'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: dcb806a213bea9d7c782eeddc712f1eb76257e80
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186402"
---
# <a name="region-c-reference"></a>#region (C# 參考)

`#region` 當您使用程式碼編輯器的 [大綱](/visualstudio/ide/outlining) 功能時，可讓您指定可展開或折迭的程式碼區塊。 在較長的程式碼檔案中，能夠摺疊或隱藏一或多個區域是很方便的，如此您可以專注於目前處理的檔案部分。 下例示範如何定義區域：  
  
```csharp
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

 `#region` 區塊必須以 [#endregion](./preprocessor-endregion.md) 指示詞結束。  
  
 `#region` 區塊不能與 [#if](./preprocessor-if.md) 區塊重疊。 不過，`#region` 區塊可以巢狀方式置於 `#if` 區塊中，而 `#if` 區塊可以巢狀方式置於 `#region` 區塊中。  
  
## <a name="see-also"></a>另請參閱

- [C # 參考](../index.md)
- [C # 程式設計指南](../../programming-guide/index.md)
- [C # 預處理器指示詞](./index.md)
