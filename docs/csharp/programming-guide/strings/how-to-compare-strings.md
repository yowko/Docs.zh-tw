---
title: "如何：比較字串 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], comparison
- comparing strings [C#]
ms.assetid: e1268e28-ee98-4695-98e9-92280f1c33c0
caps.latest.revision: 23
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 494b9ef1a1e6c8958dd3df2edb44debf32690eeb
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-compare-strings-c-programming-guide"></a>如何：比較字串 (C# 程式設計手冊)
當您比較字串時，您產生的結果會顯示一個字串是大於或小於另一個，或兩個字串相等。 決定結果的規則會隨您執行「序數比較」或「區分文化特性比較」而異。 特定工作請務必使用正確的比較類型。  
  
 當您必須比較或排序兩個字串的值，但不考慮語言慣例時，請使用基本的序數比較。 基本的序數比較 (`System.StringComparison.Ordinal`) 會區分大小寫，這表示兩個字串必須逐字元比對："and" 不等於 "And" 或 "AND"。 常用的變化是 `System.StringComparison.OrdinalIgnoreCase`，它會比對 "and"、"And" 和 "AND"。 `StringComparison.OrdinalIgnoreCase` 通常用來比較檔案名稱、路徑名稱、網路路徑，以及不會隨使用者電腦的地區設定而變更其值的任何其他字串。 如需詳細資訊，請參閱<xref:System.StringComparison?displayProperty=fullName>。  
  
 區分文化特性比較通常用於比較和排序使用者輸入的字串，因為這些字串的字元和排序慣例可能會隨使用者電腦的地區設定而異。 即使包含完全相同字元的字串，也可能因目前執行緒的文化特性而改變排序。  
  
> [!NOTE]
>  當您比較字串時，您應該使用明確指定打算執行比較類型的方法。 這可讓程式碼更容易維護及閱讀。 可能的話，請使用 <xref:System.String?displayProperty=fullName> 和 <xref:System.Array?displayProperty=fullName> 類別之方法的多載，而這些類別接受 <xref:System.StringComparison> 列舉參數，以指定要執行的比較類型。 比較字串時，最好避免使用 `==` 和 `!=` 運算子。 此外，請避免使用 <xref:System.String.CompareTo%2A?displayProperty=fullName> 執行個體方法，因為沒有任何多載接受 <xref:System.StringComparison>。  
  
## <a name="example"></a>範例  
 下例示範如何正確比較不隨使用者電腦的地區設定而變更其值的字串。 此外，它也會示範 C# 的「字串暫留」功能。 當程式宣告兩個或多個相同的字串變數時，編譯器會將它們全部儲存在相同的位置。 藉由呼叫 <xref:System.Object.ReferenceEquals%2A> 方法，您會看到兩個字串實際上參考記憶體中的相同物件。 請使用 <xref:System.String.Copy%2A?displayProperty=fullName> 方法來避免暫留，如範例中所示。  
  
 [!code-cs[csProgGuideStrings#11](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_1.cs)]  
  
## <a name="example"></a>範例  
 下列範例示範如何使用可接受 <xref:System.StringComparison> 列舉的 <xref:System.String?displayProperty=fullName> 方法，以慣用方式來比較字串。 請注意，在這裡未使用 <xref:System.String.CompareTo%2A?displayProperty=fullName> 執行個體方法，因為沒有任何多載接受 <xref:System.StringComparison>。  
  
 [!code-cs[csProgGuideStrings#31](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_2.cs)]  
  
## <a name="example"></a>範例  
 下例示範如何使用接受 <xref:System.StringComparer?displayProperty=fullName> 參數的靜態 <xref:System.Array> 方法，在陣列中以區分文化特性的方式來排序及搜尋字串。  
  
 [!code-cs[csProgGuideStrings#32](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-compare-strings_3.cs)]  
  
 項目或索引鍵的類型為 `string` 時，<xref:System.Collections.Hashtable?displayProperty=fullName>、<xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> 和 <xref:System.Collections.Generic.List%601?displayProperty=fullName> 這類集合類別具有接受 <xref:System.StringComparer?displayProperty=fullName> 參數的建構函式。 通常應該盡可能使用這些建構函式，並指定 `Ordinal` 或 `OrdinalIgnoreCase`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>   
 <xref:System.StringComparer?displayProperty=fullName>   
 [字串](../../../csharp/programming-guide/strings/index.md)   
 [比較字串](../../../standard/base-types/comparing.md)   
 [全球化和當地語系化應用程式](/visualstudio/ide/globalizing-and-localizing-applications)

