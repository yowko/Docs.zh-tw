---
title: HOW TO：判斷字串是否表示數值 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: a20850e6fc34b28975dbb2b6be819bf2e88f1f27
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244553"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>HOW TO：判斷字串是否表示數值 (C# 程式設計指南)
若要判斷字串是否為所指定數值類型的有效呈現，請使用靜態 `TryParse` 方法，而這個方法是由所有基本數字類型以及 <xref:System.DateTime> 和 <xref:System.Net.IPAddress> 此等類型所實作。 下列範例示範如何判斷 "108" 是否為有效 [int](../../../csharp/language-reference/keywords/int.md)。  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 如果字串包含非數值字元，或所指定之特定類型的數值太大或太小，則 `TryParse` 會傳回 false，並將 out 參數設定為零。 否則會傳回 true，並將 out 參數設定為字串的數值。  
  
> [!NOTE]
>  字串只能包含數值字元，而且仍然不適用於您所使用 `TryParse` 方法的類型。 例如，"256" 不是 `byte` 的有效值，但為 `int` 的有效值。 "98.6" 不是 `int` 的有效值，但為有效的 `decimal`。  
  
## <a name="example"></a>範例  
 下列範例示範如何搭配使用 `TryParse` 與 `long`、`byte` 和 `decimal` 值的字串呈現。  
  
 [!code-csharp[csProgGuideStrings#14](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-determine-whether-a-string-represents-a-numeric-value_1.cs)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 基本數值類型也會實作 `Parse` 靜態方法，但如果字串不是有效數字，則會擲回例外狀況。 `TryParse` 通常更具效率，因為它在數字不正確時就會傳回 false。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 請一律使用 `TryParse` 或 `Parse` 方法來驗證文字方塊和下拉式方塊這類控制項的使用者輸入。  
  
## <a name="see-also"></a>請參閱

- [如何：將位元組陣列轉換為成整數](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)  
- [如何：將字串轉換為數值](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)  
- [如何：在十六進位字串和數字類型間轉換](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)  
- [剖析數值字串](../../../standard/base-types/parsing-numeric.md)  
- [格式化類型](../../../standard/base-types/formatting-types.md)
