---
title: "System.Uri 的國際資源識別項支援 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: b5e994c3-3535-4aff-8e1b-b69be22e9a22
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# System.Uri 的國際資源識別項支援
<xref:System.Uri?displayProperty=fullName> 類別擴充了 International Resource Identifier \(IRI\) 和國際化網域名稱 \(IDN\) \(IDN\) 支援。  這些增強功能可在 .NET Framework 3.5、3.0 SP1 和 2.0 SP1。  
  
## IRI 和 IDN 支援  
 網站位址一般用來表示由極有限的一組字元的統一資源識別元 \(URI\) \(URI\):  
  
-   英文字母的大小寫 ASCII 字母。  
  
-   0 到 9 的數字。  
  
-   少部分的其他 ASCII 符號。  
  
 URI 規格記載在網際網路工程任務推動小組 \(Internet Engineering Task Force，\(IETF\)\) 發行的 RFC 2396 和 RFC 3986 中。  
  
 隨著網際網路的成長，使用非英文語言來識別資源的需求也跟著增加。  而簡化這個需求並允許非 ASCII 字元 \(Unicode\/ISO 10646 字元集中的字元集 \(Character Set\)\) 的識別項稱為「國際資源識別項」\(International Resource Identifier，IRI\)。  IRI 規格記載在 IETF 發行的 RFC 3987 中。  使用 IRI 可以讓 URL 包含 Unicode 字元。  
  
 現有的 <xref:System.Uri?displayProperty=fullName> 類別會擴充提供依據 RFC 3987 的 IRI 支援。  除非特別啟用 IRI，否則目前的使用者並不會看到 .NET Framework 2.0 的行為有任何變化。  這可確保應用程式與舊版 .NET Framework 的相容性。  
  
 應用程式是否可以使用指定的國際化網域名稱 \(IDN\) 解析套用至網域名稱，以及是否應該套用 IRI 剖析規則。  這項變更可以在 machine.config 或 app.config 檔案中進行。  
  
 啟用 IDN 會將網域名稱內的所有 Unicode 標籤 \(Label\) 轉換成 Punycode 的對等名稱。  Punycode 名稱只包含 ASCII 字元，且開頭一律為 xn\-\- 前置字元。  這麼做的原因是要支援網際網路上現有的 DNS 伺服器，因為大多數的 DNS 伺服器僅支援 ASCII 字元 \(請參閱 RFC 3940\)。  
  
 啟用 IRI 和 IDN 會影響 <xref:System.Uri.DnsSafeHost%2A?displayProperty=fullName> 屬性的值。  啟用 IRI 和 IDN 也會變更 <xref:System.Uri.Equals%2A?displayProperty=fullName>、<xref:System.Uri.OriginalString%2A?displayProperty=fullName>、<xref:System.Uri.GetComponents%2A?displayProperty=fullName> 和 <xref:System.Uri.IsWellFormedOriginalString%2A> 方法的行為。  
  
 也已擴充 <xref:System.GenericUriParser?displayProperty=fullName> 類別，允許建立支援 IRI 和 IDN 的可自訂剖析器 \(Parser\)。  將 <xref:System.GenericUriParserOptions?displayProperty=fullName> 列舉型別 \(Enumeration\) 中可用值的位元 \(Bitwise\) 組合傳遞給 <xref:System.GenericUriParser?displayProperty=fullName> 建構函式，就可以指定 <xref:System.GenericUriParser?displayProperty=fullName> 物件的行為。  <xref:System.GenericUriParserOptions?displayProperty=fullName> 型別表示剖析器支援在 RFC 3987 中，針對國際資源識別元 \(IRI\) 指定的剖析規則。  實際上是否使用 IRI 而定，如果啟用 IRI。  
  
 <xref:System.GenericUriParserOptions?displayProperty=fullName> 型別表示剖析器支援國際化網域名稱 \(IDN\) 剖析主機名稱的 \(IDN\)。  實際上是否使用 IDN 而定，如果啟用 IDN。  
  
 啟用 IRI 剖析會根據 RFC 3987 中最新的 IRI 規則執行正規化和字元。  預設值為 IRI 剖析停用，因此字元檢查根據 RFC 2396 和 RFC 3986 完成。  
  
 處理在 <xref:System.Uri?displayProperty=fullName> 類別中的 IRI 和 IDN 也進行控制使用 <xref:System.Configuration.IriParsingElement?displayProperty=fullName> 和 <xref:System.Configuration.IdnElement?displayProperty=fullName> 組態設定類別。  <xref:System.Configuration.IriParsingElement?displayProperty=fullName> 設定可啟用或停用 <xref:System.Uri?displayProperty=fullName> 類別中的 IRI 處理。  <xref:System.Configuration.IdnElement?displayProperty=fullName> 設定則可啟用或停用 <xref:System.Uri> 類別中的 IDN 處理。  <xref:System.Configuration.IriParsingElement?displayProperty=fullName> 設定也可間接控制 IDN。  必須啟用 IRI 處理，才能執行 IDN 處理。  如果停用 IRI 處理，則 IDN 處理會設定為預設設定，此時為考量相容性會使用 .NET Framework 2.0 的行為，且不會使用 IDN 名稱。  
  
 如果第一 <xref:System.Uri?displayProperty=fullName> 類別中建構， <xref:System.Configuration.IriParsingElement?displayProperty=fullName> 和 <xref:System.Configuration.IdnElement?displayProperty=fullName> 組態類別的組態設定會讀取一次  過了這個時間之後，對組態設定所做的變更都會被忽略。  
  
## 請參閱  
 <xref:System.Configuration.IdnElement?displayProperty=fullName>   
 <xref:System.Configuration.IriParsingElement?displayProperty=fullName>   
 <xref:System.Uri?displayProperty=fullName>   
 <xref:System.Uri.DnsSafeHost%2A?displayProperty=fullName>