---
title: "如何：將時區儲存到內嵌資源 | Microsoft Docs"
ms.custom: ""
ms.date: "04/10/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "時區物件 [.NET Framework], 儲存"
  - "時區物件 [.NET Framework], 序列化"
  - "時區 [.NET Framework], 儲存"
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：將時區儲存到內嵌資源
時區感知應用程式通常需要特定的時區。  但是，因為個別 <xref:System.TimeZoneInfo> 物件的可用性必須視本機系統登錄中所儲存的資訊而定，所以即使自訂可用的時區也可能不存在。  此外，使用 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 方法具現化的自訂時區相關資訊，並不會和其他時區資訊一起儲存在登錄中。  如果要確保這些時區在需要時可以使用，您可以將時區序列化加以儲存，稍後再還原序列化以還原時區。  
  
 一般而言，將 <xref:System.TimeZoneInfo> 物件序列化與時區感知應用程式無關。  視用來保存序列化 <xref:System.TimeZoneInfo> 物件的資料存放區而定，時區資料可能會被序列化成為設定或安裝常式的一部分 \(例如，當資料儲存在登錄的應用程式索引鍵中\)，或成為編譯最終應用程式前所執行的公用程式常式的一部分 \(例如，當序列化資料存放在 .NET XML 資源 \(.resx\) 檔中時\)。  
  
 除了以應用程式編譯的資源檔外，還有幾個其他資料存放區可用來存放時區資訊。  這些需求包括下列各項：  
  
-   登錄。  請注意，應用程式應使用自己的應用程式索引鍵的子機碼，儲存自訂時區資料，而不是使用 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\Time Zones 的子機碼。  
  
-   組態檔。  
  
-   其他系統檔案。  
  
### 將時區序列化成 .resx 檔案以儲存時區  
  
1.  擷取現有時區，或建立新的時區。  
  
     如果要擷取現有時區，請參閱 [如何：存取預先定義的 UTC 和本機時區物件](../../../docs/standard/datetime/access-utc-and-local.md)及 [如何：具現化 TimeZoneInfo 物件](../../../docs/standard/datetime/instantiate-time-zone-info.md)。  
  
     如果要建立新的時區，請呼叫下列 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 方法的其中一個多載。  如需詳細資訊，請參閱[如何：建立沒有調整規則的時區](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)與[如何：建立有調整規則的時區](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)。  
  
2.  呼叫 <xref:System.TimeZoneInfo.ToSerializedString%2A> 方法以建立內含時區資料的字串。  
  
3.  提供 .resx 檔案的名稱 \(或路徑\) 給 <xref:System.IO.StreamWriter> 類別建構函式，將 <xref:System.IO.StreamWriter> 物件具現化。  
  
4.  將 <xref:System.IO.StreamWriter> 物件傳送給 <xref:System.Resources.ResXResourceWriter> 類別建構函式，將 <xref:System.Resources.ResXResourceWriter> 物件具現化。  
  
5.  將時區的序列化字串傳送給 <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=fullName> 方法。  
  
6.  呼叫 <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=fullName> 方法。  
  
7.  呼叫 <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=fullName> 方法。  
  
8.  呼叫 <xref:System.IO.StreamWriter> 物件的 <xref:System.IO.StreamWriter.Close%2A> 方法，即可關閉物件。  
  
9. 將產生的 .resx 檔案新增至應用程式的 Visual Studio 專案中。  
  
10. 使用 Visual Studio 中的 \[**屬性**\] 視窗，確認 .resx 檔案的 \[**建置動作**\] 屬性設定為 \[**內嵌資源**\]。  
  
## 範例  
 下列範例將代表「中央標準時間」的 <xref:System.TimeZoneInfo> 物件，以及代表「南極科學研究站」時間的 <xref:System.TimeZoneInfo> 物件，序列化成名稱為 SerializedTimeZones.resx 的 .NET XML 資源檔。  「中央標準時間」通常定義在登錄中，「南極科學研究站」則是自訂時區。  
  
 [!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
 [!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]  
  
 這個範例會將 <xref:System.TimeZoneInfo> 物件序列化，這樣編譯時資源檔就可以使用。  
  
 因為 <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=fullName> 方法會將完整的標頭資訊新增至 .NET XML 資源檔，所以不能用來將資源新增至現有檔案。  範例中處理的方法，是檢查 SerializedTimeZones.resx 檔案，如果有這個檔案，則除了這兩個序列化的時區外，會將所有其他資源儲存至泛型 <xref:System.Collections.Generic.Dictionary%602> 物件。  然後就會刪除現有檔案，新增現有資源至新的 SerializedTimeZones.resx 檔案。  序列化的時區資料也會新增至這個檔案。  
  
 資源的索引鍵 \(或 \[**名稱**\]\) 欄位不應包含空白字元。  在時區識別項被指派給資源檔前，呼叫 <xref:System.String.Replace%28System.String%2CSystem.String%29> 方法以移除識別項中所有的空白字元。  
  
## 編譯程式碼  
 這個範例需要：  
  
-   將 System.Windows.Forms.dll 的參考及 System.Core.dll 新增至專案。  
  
-   匯入下列命名空間：  
  
     [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
     [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]  
  
## 請參閱  
 [日期、時間和時區](../../../docs/standard/datetime/index.md)   
 [時區概觀](../../../docs/standard/datetime/time-zone-overview.md)   
 [如何：從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)