---
title: "如何：在舊版編碼方式和 Unicode 間轉換 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "轉換 [C#], 從舊版轉換成 Unicode 編碼方式"
  - "字串 [C#], 編碼方式之間的轉換"
ms.assetid: 4eed7d8e-47ab-4a7c-8b95-9645a0ef000b
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# 如何：在舊版編碼方式和 Unicode 間轉換 (C# 程式設計手冊)
在 C\# 中，所有記憶體內的字串編碼都是 Unicode \(UTF\-16\)。  當您將資料從儲存區帶入 `string` 物件時，資料會自動轉換成 UTF\-16。  如果資料只包含 0 到 127 的 ASCII 值，您就不需要額外進行轉換。  不過，如果原始程式文字包含延伸 ASCII 位元組值 \(128 到 255\)，則預設會按照目前的字碼頁 \(Code Page\) 來解譯擴充字元。  若要指定按照不同字碼頁來解譯原始程式文字，請使用 <xref:System.Text.Encoding?displayProperty=fullName> 類別 \(Class\)，如下列範例所示。  
  
## 範例  
 在下列範例中，會示範如何轉換已編碼為 8 位元 ASCII 的文字檔，並按照 Windows 字碼頁 737 來解譯原始程式文字。  
  
 [!code-cs[csProgGuideStrings#34](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-between-legacy-encodings-and-unicode_1.cs)]  
  
## 請參閱  
 [字串](../../../csharp/programming-guide/strings/index.md)