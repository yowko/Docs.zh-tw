---
title: "如何：判斷字串是否表示數值 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
caps.latest.revision: 9
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
ms.openlocfilehash: d2f89f4a4771625389a04f5c92829c91d66eb207
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 如何：判斷字串是否表示數值 (C# 程式設計手冊)
若要判斷字串是否為指定之數字型別 \(Numeric Type\) 的有效表示，請使用靜態 `TryParse` 方法，這是由所有基本數字型別以及 <xref:System.DateTime> 和 <xref:System.Net.IPAddress> 等這類型別實作的方法。  下列範例顯示如何判斷 "108" 是否為有效的 [int](../../../csharp/language-reference/keywords/int.md)。  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 如果字串包含非數字字元或者數值對於您指定的特定型別而言太大或太小，`TryParse` 會傳回 false 並且將 out 參數設為零。  否則，會傳回 true 並且將 out 參數設為字串的數值。  
  
> [!NOTE]
>  字串可能只包含數字字元，並且對於您使用其 `TryParse` 方法的型別而言仍然是無效的。  例如，"256" 不是 `byte` 的有效值，但卻是 `int` 的有效值。 「  "98.6" 不是 `int` 的有效值，但卻是 `decimal` 的有效值。  
  
## 範例  
 下列範例顯示如何使用 `TryParse` 與 `long`、`byte` 及 `decimal` 值的字串表示。  
  
 [!code-cs[csProgGuideStrings#14](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-determine-whether-a-string-represents-a-numeric-value_1.cs)]  
  
## 穩固程式設計  
 基本數字類資料型別也會實作 `Parse` 靜態方法，在字串不是有效數字時擲回例外狀況。  `TryParse` 較為有效，因為它在數字無效時只會傳回 false。  
  
## .NET Framework 安全性  
 一律使用 `TryParse` 或 `Parse` 方法驗證控制項的使用者輸入，例如文字方塊和下拉式方塊。  
  
## 請參閱  
 [如何：將位元組陣列轉換成整數](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)   
 [如何：將字串轉換為數值](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)   
 [如何：在十六進位字串和數字類型間轉換](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)   
 [剖析數值字串](../../../standard/base-types/parsing-numeric.md)   
 [格式化類型](../../../standard/base-types/formatting-types.md)

