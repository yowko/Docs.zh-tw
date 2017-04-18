---
title: "如何：在日期與時間值中顯示毫秒 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "日期 [.NET Framework], 毫秒"
  - "DateTime.ToString 方法"
  - "顯示日期和時間資料"
  - "毫秒 [.NET Framework]"
  - "時間 [.NET Framework], 毫秒"
ms.assetid: ae1a0610-90b9-4877-8eb6-4e30bc5e00cf
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：在日期與時間值中顯示毫秒
預設的日期和時間格式化方法 \(例如 <xref:System.DateTime.ToString?displayProperty=fullName>\) 包括時間值的時、分和秒，但不包括毫秒元件。  本主題將說明如何將日期和時間的毫秒元件加入格式化的日期和時間字串中。  
  
### 顯示 DateTime 值的毫秒元件  
  
1.  如果您使用的是日期的字串表示，請使用靜態 <xref:System.DateTime.Parse%28System.String%29?displayProperty=fullName> 或 <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=fullName> 方法，將它轉換成 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 值。  
  
2.  若要擷取時間毫秒元件的字串表示，請呼叫日期和時間值的 <xref:System.DateTime.ToString%28System.String%29?displayProperty=fullName> 或是 <xref:System.DateTimeOffset.ToString%2A> 方法，並且單獨傳遞 `fff` 或 `FFF` 自訂格式模式，或是連同其他自訂格式規範一併傳遞做為 `format` 參數。  
  
## 範例  
 這個範例會對主控台單獨顯示 <xref:System.DateTime> 的毫秒元件和 <xref:System.DateTimeOffset> 值，且兩者都會包含在較長的日期和時間字串中。  
  
 [!code-csharp[Formatting.HowTo.Millisecond#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#1)]
 [!code-vb[Formatting.HowTo.Millisecond#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#1)]  
  
 `fff` 格式模式會包含毫秒值中任何結尾的零。  `FFF` 格式模式則會隱藏結尾的零。  以下範例會說明兩者之間的差異。  
  
 [!code-csharp[Formatting.HowTo.Millisecond#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#2)]
 [!code-vb[Formatting.HowTo.Millisecond#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#2)]  
  
 定義包含日期和時間之毫秒元件的完整格式規範會發生的問題在於，它會定義硬式編碼格式，而該格式可能不會對應到應用程式目前文化特性中時間項目的排列。  較佳的替代方案是擷取目前文化特性的 <xref:System.Globalization.DateTimeFormatInfo> 物件所定義的其中一個日期和時間顯示模式，並且修改該模式以納入毫秒。  這個範例也會說明這個方法。  這個方法會從 <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=fullName> 屬性擷取目前文化特性的完整日期和時間模式，然後在其秒模式後面插入自訂的模式 `.ffff`。  請注意，範例中會使用規則運算式在單一方法呼叫中執行這項操作。  
  
 除了毫秒之外，您也可以使用自訂格式規範顯示秒的其他小數部分。  例如，`f` 或 `F` 自訂格式規範會顯示秒的十分位數，`ff` 或 `FF` 自訂格式規範會顯示秒的百分位數，而 `ffff` 或 `FFFF` 自訂格式規範則會顯示秒數小數點後的四位數字。  毫秒的小數部分會截斷，而不會進位到傳回的字串中。  這些格式規範會在下面的範例中使用。  
  
 [!code-csharp[Formatting.HowTo.Millisecond#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#3)]
 [!code-vb[Formatting.HowTo.Millisecond#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#3)]  
  
> [!NOTE]
>  另外，也可以顯示非常小的秒數小數單位，例如，秒數小數點後的四位數或五位數。  不過，這些值可能沒有太大的意義。  日期和時間值的精確度會根據系統時鐘的解析度而定。  在 Windows NT 3.5 \(含\) 以後版本及 [!INCLUDE[windowsver](../../../includes/windowsver-md.md)] 作業系統上，時鐘的解析度大約為 10\-15 毫秒。  
  
## 編譯程式碼  
 使用 csc.exe 或 vb.exe 在命令列編輯程式碼。  若要編譯 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中的程式碼，請將程式碼放在主控台應用程式專案範本中。  
  
## 請參閱  
 <xref:System.Globalization.DateTimeFormatInfo>   
 [自訂日期和時間格式字串](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)