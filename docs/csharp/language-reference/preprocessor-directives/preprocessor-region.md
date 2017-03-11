---
title: "#region (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "#region"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#region 指示詞 [C#]"
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
caps.latest.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 12
---
# #region (C# 參考)
`#region` 可讓您指定在使用 Visual Studio 程式碼編輯器的[大綱](/visual-studio/ide/outlining)功能時，可以展開或摺疊的程式碼區塊。  在程式碼較常的檔案中，如果可以摺疊或隱藏一個或多個區域會更加方便，因為如此一來，您可以專注在目前工作的檔案內容上。  下列範例會示範如何定義一個區域：  
  
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
  
## 備註  
 `#region` 區塊必須以 [\#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) 指示詞結束。  
  
 `#region` 區塊不能與 [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) 區塊重疊。  但是 `#region` 區塊可以巢狀出現在 `#if` 區塊中，而 `#if` 區塊可以巢狀出現在 `#region` 區塊中。  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)