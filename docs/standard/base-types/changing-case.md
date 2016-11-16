---
title: "變更大小寫"
description: "變更大小寫"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 646c5afd-8aec-4393-9c00-f68ad2580c68
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: a6f6f21daae79f752cfac0a70558778ae98d1a5d

---

# <a name="changing-case"></a>變更大小寫

如果您要撰寫接受使用者輸入的應用程式，則無法確定使用者輸入資料時會使用大寫或小寫。 通常，您會希望字串的大小寫一致，特別是要在使用者介面中顯示這些字串時。 下表描述兩種變更大小寫的方法。

方法名稱 | 用法
----------- | ---
[String.ToUpper](xref:System.String.ToUpper) | 將字串中的所有字元轉換成大寫。
[String.ToLower](xref:System.String.ToLower) | 將字串中的所有字元轉換成小寫。

> [!WARNING]  
> 請注意，您不應該使用 `String.ToUpper` 和 `String.ToLower` 方法來轉換字串，以便對字串進行比較或測試字串是否相等。 

## <a name="comparing-strings-of-mixed-case"></a>比較混合大小寫的字串

若要比較混合大小寫的字串以決定字串是否相等，請使用 *comparisonType* 參數呼叫 [String](xref:System) `Equals` 方法的其中一個多載，並為 *comparisonType* 引數提供 [StringComparison.CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase) 或 [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) 的值。 

如需詳細資訊，請參閱[使用字串的最佳做法](best-practices.md)。 

## <a name="toupper"></a>ToUpper

[String.ToUpper](xref:System.String.ToUpper) 方法會將字串中的所有字元變更為大寫。 下列範例會將字串 "Hello World!" 從混合大小寫轉換成大寫。

```csharp
string properString = "Hello World!";
Console.WriteLine(properString.ToUpper());
// This example displays the following output:
//       HELLO WORLD!
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.ToUpper())
' This example displays the following output:
'       HELLO WORLD!
```

## <a name="tolower"></a>ToLower

[String.ToLower](xref:System.String.ToLower) 方法類似於前一個方法，但會改將字串中的所有字元轉換成小寫。 下列範例會將字串 "Hello World!" 轉換成小寫。

```csharp
string properString = "Hello World!";
Console.WriteLine(properString.ToLower());
// This example displays the following output:
//       hello world!
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.ToLower())
' This example displays the following output:
'       hello world!
```

## <a name="see-also"></a>另請參閱

[基本字串作業](basic-string-operations.md)



<!--HONumber=Nov16_HO1-->


