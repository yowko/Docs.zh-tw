---
title: "常值 (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 092ef693-6e5f-41b4-b868-5b9e82928abf
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 常值 (Entity SQL)
本主題將描述常值 \(Literal\) 的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 支援。  
  
## Null  
 Null 常值是用來代表任何型別的 null 值。  Null 常值與任何型別都相容。  
  
 您可以透過 null 常值的轉換作業建立 null 型別。  如需詳細資訊，請參閱[CAST](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)。  
  
 如需可以自由使用浮動 null 常值之位置的相關規則，請參閱 [Null 常值和類型推斷](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md)。  
  
## Boolean  
 布林常值是由 `true` 和 `false` 關鍵字代表。  
  
## Integer  
 整數常值可以屬於 <xref:System.Int32> 或 <xref:System.Int64> 型別。  <xref:System.Int32> 常值是一連串數字字元。  <xref:System.Int64> 常值是一連串數字字元，後面接著大寫 L。  
  
## Decimal  
 固定點數 \(十進位\) 是一連串數字字元、一個點 \(.\) 和另一連串數字字元，後面接著大寫的「M」。  
  
## 單精確度浮點數、雙精確度浮點數  
 雙精確度浮點數是一連串數字字元、小數點 \(.\) 和另一串數字字元，後面可能接著指數。  單精確度浮點數 \(或浮點數 \(Float\)\) 是雙精確度浮點數語法，後面接著小寫 f。  
  
## String  
 字串是以引號括住的一連串字元。  引號可以是兩個單引號 \(`'`\) 或兩個雙引號 \("\)。  字元字串常值可以是 Unicode 或非 Unicode。  如果要將字元字串常值宣告為 Unicode，請在此常值將會加上一個大寫的 "N"。  預設值為非 Unicode 字元字串常值。  在 N 和此字串常值裝載之間可以不空格，但 N 必須是大寫。  
  
```  
'hello' -- non-Unicode character string literal  
N'hello' -- Unicode character string literal  
"x"  
N"This is a string!"  
'so is THIS'  
```  
  
## DateTime  
 日期時間常值與地區設定 \(Locale\) 無關，而且它是由日期部分和時間部分所組成。  日期和時間部分都是強制的，而且沒有任何預設值。  
  
 日期部分的格式必須是：`YYYY`\-`MM`\-`DD`，其中 `YYYY` 是四位數字的年份，值介於 0001 到 9999 之間；`MM` 是月份，值介於 1 到 12 之間；而`DD` 則是所指定月份 `MM` 中的有效日數。  
  
 時間部分的格式必須是 `HH`:`MM`\[:`SS`\[.fffffff\]\]，其中 `HH`是小時值，介於 0 到 23 之間、`MM`是分鐘值，介於 0 到 59 之間、`SS`是秒鐘值，介於 0 到 59 之間，而 fffffff 則是秒鐘的小數部分，值介於 0 到 9999999 之間。  以上所有值的範圍都包含在內。  秒鐘的小數部分則為選擇性。  除非已指定秒鐘的小數部分，否則秒鐘亦為選擇性；但指定秒鐘的小數部分時，則必須有秒鐘。  如果未指定秒鐘或秒鐘的小數部分，則會使用預設值 0。  
  
 DATETIME 符號與常值裝載之間可以有任何數目的空格，但是不能有新行。  
  
```  
DATETIME'2006-10-1 23:11'  
DATETIME'2006-12-25 01:01:00.0000000' -- same as DATETIME'2006-12-25 01:01'  
```  
  
## 時間  
 時間常值會依地區設定而異，而且僅由時間部分組成。  時間部分為必要項，而且沒有預設值。  它必須是 HH:MM\[:SS\[.fffffff\]\] 格式，其中 HH 是小時，值介於 0 到 23 之間；MM 是分鐘，值介於 0 到 59 之間；SS 是秒鐘，值介於 0 到 59 之間；而 fffffff 則是秒鐘的小數部分，值介於 0 到 9999999 之間。  以上所有值的範圍都包含在內。  秒鐘的小數部分則為選擇性。  除非已指定秒鐘的小數部分，否則秒鐘亦為選擇性；但指定秒鐘的小數部分時，則必須有秒鐘。  如果未指定秒鐘或秒鐘的小數部分，則會使用預設值 0。  
  
 TIME 符號與常值裝載之間可以有任何數目的空格，但是不能有新行。  
  
```  
TIME‘23:11’  
TIME‘01:01:00.1234567’  
```  
  
## DateTimeOffset  
 datetimeoffset 常值會依地區設定而異，而且是由日期部分、時間部分和時差部分組成。  所有日期、時間和時差部分都是必要項，而且沒有預設值。  日期部分必須是 YYYY\-MM\-DD 格式，其中 YYYY 是四位數字的年份，值介於 0001 到 9999 之間；MM 是月份，值介於 1 到 12 之間；而 DD 則是所指定月份中的有效日數。  時間部分必須是 HH:MM\[:SS\[.fffffff\]\] 格式，其中 HH 是小時，值介於 0 到 23 之間；MM 是分鐘，值介於 0 到 59 之間；SS 是秒鐘，值介於 0 到 59 之間；而 fffffff 則是秒鐘的小數部分，值介於 0 到 9999999 之間。  以上所有值的範圍都包含在內。  秒鐘的小數部分則為選擇性。  除非已指定秒鐘的小數部分，否則秒鐘亦為選擇性；但指定秒鐘的小數部分時，則必須有秒鐘。  如果未指定秒鐘或秒鐘的小數部分，則會使用預設值 0。  時差部分必須是 {\+&#124;\-}HH:MM 格式，其中 HH 和 MM 的意義與時間部分相同。  不過時差的範圍必須介於 \-14:00 到 \+ 14:00 之間  
  
 DATETIMEOFFSET 符號與常值裝載之間可以有任何數目的空格，但是不能有新行。  
  
```  
DATETIMEOFFSET‘2006-10-1 23:11 +02:00’  
DATETIMEOFFSET‘2006-12-25 01:01:00.0000000 -08:30’  
```  
  
> [!NOTE]
>  有效的 Entity SQL 常值可能會落在 CLR 或資料來源支援的範圍之外。  這種情況可能會造成例外狀況  
  
## 二元  
 二進位字串常值是以單引號分隔的一連串十六進位數字，後面跟著關鍵字 binary 或捷徑符號 `X` 或 `x`。  捷徑符號 `X` 不區分大小寫。  關鍵字 `binary` 與二進位字串值之間允許使用零個或多個空格。  
  
 十六進位字元也不區分大小寫。  如果此常值所包含的十六進位數是奇數，系統就會在常值前面加上一個十六進位零位數，讓此常值與下一個偶數的十六進位數對齊。  二進位字串的大小沒有正式的限制。  
  
```  
Binary'00ffaabb'  
X'ABCabc'  
BINARY    '0f0f0f0F0F0F0F0F0F0F'  
X'' –- empty binary string  
```  
  
## Guid  
 `GUID` 常值代表全域唯一的識別碼。  它是以關鍵字 `GUID` 格式化的序列，後面跟著稱為「*登錄*」\(Registry\) \(以單引號括住的 8\-4\-4\-4\-12 格式\) 的十六進位數字。  十六進位數不區分大小寫。  
  
 GUID 符號與常值裝載之間可以有任何數目的空格，但是不能有新行。  
  
```  
Guid'1afc7f5c-ffa0-4741-81cf-f12eAAb822bf'  
GUID  '1AFC7F5C-FFA0-4741-81CF-F12EAAB822BF'  
```  
  
## 請參閱  
 [Entity SQL 概觀](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)