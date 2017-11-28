---
title: "如何：修改字串內容 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: strings [C#], modifying
ms.assetid: b6c20bba-ce22-43d7-ad1b-5ce65f714055
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b0810d5722c2c32f7884187bb2e3fc5a039825c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-string-contents-c-programming-guide"></a>如何：修改字串內容 (C# 程式設計手冊)
由於字串「不可變」，所以不可能 (不使用不安全的程式碼) 在建立後修改字串物件的值。 不過，有許多方法可以修改字串值，並將結果儲存在新的字串物件中。 <xref:System.String?displayProperty=nameWithType> 類別會提供在輸入字串上運作的方法，並傳回新的字串物件。 在許多情況下，您可以將新的物件指派給保留原始字串的變數。 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> 類別會提供其他以類似方式運作的方法。 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 類別提供您可以「就地」修改的字元緩衝區。 您呼叫 <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> 方法建立的新字串物件，包含目前的緩衝區內容。  
  
## <a name="example"></a>範例  
 下例示範各種方式，取代或移除指定字串中的子字串。  
  
 [!code-csharp[csProgGuideStrings#28](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_1.cs)]  
  
## <a name="example"></a>範例  
 若要使用陣列標記法來存取字串中的個別字元，您可以使用 <xref:System.Text.StringBuilder> 物件，多載 `[]` 運算子以存取其內部的字元緩衝區。 您也可以使用 <xref:System.String.ToCharArray%2A> 方法，將字串轉換成字元陣列。 下例會使用 `ToCharArray` 建立陣列。 然後就會修改此陣列的某些元素。 將字元陣列當做輸入參數的字串建構函式，接著會被呼叫以建立新的字串。  
  
 [!code-csharp[csProgGuideStrings#24](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_2.cs)]  
  
## <a name="example"></a>範例  
 下列範例是針對極其罕見的情況：您可能想要以類似 C 樣式字元陣列的方式，使用不安全的程式碼就地修改字串。 本例示範如何使用 fixed 關鍵字「就地」存取個別字元。 它也示範因為 C# 編譯器在內部儲存 (實習生) 字串的方式，可能造成的字串不安全作業的一個副作用。 一般情況下，除非絕對必要，您不應該使用這項技術。  
  
 [!code-csharp[csProgGuideStrings#29](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_3.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [字串](../../../csharp/programming-guide/strings/index.md)
