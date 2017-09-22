---
title: "System.Uri 的國際資源識別項支援"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: b5e994c3-3535-4aff-8e1b-b69be22e9a22
caps.latest.revision: 9
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bb81ee9db5c4c8dc7dfa9a7a193adf47ee37b604
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---
# <a name="international-resource-identifier-support-in-systemuri"></a>System.Uri 的國際資源識別項支援
<xref:System.Uri?displayProperty=fullName> 類別已擴充加上國際資源識別碼 (IRI) 和國際化網域名稱 (IDN) 支援。 NET Framework 3.5、3.0 SP1 和 2.0 SP1 皆可使用這些增強功能。  
  
## <a name="iri-and-idn-support"></a>IRI 和 IDN 支援  
 網址通常是使用統一資源識別碼 (URI) 來表示，而 URI 是由非常有限的字元組構成：  
  
-   大寫和小寫的英文 ASCII 字母。  
  
-   0 到 9 位數。  
  
-   少數幾個其他 ASCII 符號。  
  
 網際網路工程任務推動小組 (IETF) 發行的 RFC 2396 和 RFC 3986 中有記載 URI 的規格。  
  
 隨著網際網路的成長，識別使用非英文語言資源的需求也持續成長。 有利此需求且允許非 ASCII 字元 (Unicode/ISO 10646 字元集中的字元) 的識別碼，稱為國際資源識別碼 (IRI)。 IETF 發行的 RFC 3987 中有記載 IRI 的規格。 使用 IRI 可讓 URL 包含 Unicode 字元。  
  
 已擴充現有的 <xref:System.Uri?displayProperty=fullName> 類別，根據 RFC 3987 提供 IRI 支援。 目前的使用者除非特別啟用 IRI，否則看不出與 .NET Framework 2.0 的行為有任何不同之處。 這可確保應用程式與舊版 .NET framework 相容。  
  
 應用程式可以指定是否使用網域名稱套用的國際化網域名稱 (IDN) 剖析功能，以及是否應套用 IRI 剖析規則。 此作業可在 machine.config 或 app.config 檔案中完成。  
  
 啟用 IDN 會將網域名稱中所有的 Unicode 標籤轉換成對等的 Punycode。 Punycode 名稱只包含 ASCII 字元，而且開頭一律為前置詞 xn--。 這是為了支援網際網路上現有的 DNS 伺服器，因為大部分的 DNS 伺服器僅支援 ASCII 字元 (請參閱 RFC 3940)。  
  
 啟用 IRI 和 IDN 會影響 <xref:System.Uri.DnsSafeHost%2A?displayProperty=fullName> 屬性的值。 啟用 IRI 和 IDN 也可以變更 <xref:System.Uri.Equals%2A?displayProperty=fullName>、<xref:System.Uri.OriginalString%2A?displayProperty=fullName>、<xref:System.Uri.GetComponents%2A?displayProperty=fullName> 和 <xref:System.Uri.IsWellFormedOriginalString%2A> 方法的行為。  
  
 <xref:System.GenericUriParser?displayProperty=fullName> 類別也已經擴充，允許建立可自訂的剖析器，支援 IRI 和 IDN。 指定 <xref:System.GenericUriParser?displayProperty=fullName> 物件行為的方法，是將 <xref:System.GenericUriParserOptions?displayProperty=fullName> 列舉中的可用值位元組合傳遞至 <xref:System.GenericUriParser?displayProperty=fullName> 建構函式。 <xref:System.GenericUriParserOptions.IriParsing?displayProperty=fullName> 類型，指出支援 RFC 3987 指定的國際資源識別碼 (IRI) 剖析規則的剖析器。 實際是否使用 IRI，取決於是否已啟用 IRI。  
  
 <xref:System.GenericUriParserOptions.Idn?displayProperty=fullName> 類型，指出剖析器支援主機名稱的國際化網域名稱 (IDN) 剖析。 實際是否使用 IDN，取決於是否已啟用 IDN。  
  
 啟用 URI 剖析會根據 RFC 3987 中最新的 IRI 規則來執行正規化和字元檢查。 預設值專供要停用的 IRI 剖析使用，以便正規化和字元檢查根據 RFC 2396 和 RFC 3986 完成。  
  
 <xref:System.Uri?displayProperty=fullName> 類別中的 IRI 和 IDN 處理也可以使用 <xref:System.Configuration.IriParsingElement?displayProperty=fullName> 和 <xref:System.Configuration.IdnElement?displayProperty=fullName> 組態設定類別來控制。 <xref:System.Configuration.IriParsingElement?displayProperty=fullName> 設定可啟用或停用 <xref:System.Uri?displayProperty=fullName> 類別中的 IRI 處理。 <xref:System.Configuration.IdnElement?displayProperty=fullName> 設定可啟用或停用 <xref:System.Uri> 類別中的 IDN 處理。 <xref:System.Configuration.IriParsingElement?displayProperty=fullName> 設定也可以間接控制 IDN。 必須啟用 IRI 處理才能進行 IDN 處理。 如果停用 IRI 處理，則 IDN 處理會設定為預設設定，此種情況下，.NET Framework 2.0 行為會用於相容性，但不使用 IDN 名稱。  
  
 建構第一個 <xref:System.Uri?displayProperty=fullName> 類別時，<xref:System.Configuration.IriParsingElement?displayProperty=fullName> 和 <xref:System.Configuration.IdnElement?displayProperty=fullName> 組態類別的組態設定會讀取一次。 該時間之後的組態設定變更會被忽略。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Configuration.IdnElement?displayProperty=fullName>   
 <xref:System.Configuration.IriParsingElement?displayProperty=fullName>   
 <xref:System.Uri?displayProperty=fullName>   
 <xref:System.Uri.DnsSafeHost%2A?displayProperty=fullName>

