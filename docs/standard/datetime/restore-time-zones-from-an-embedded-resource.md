---
title: "如何：從內嵌資源還原時區 | Microsoft Docs"
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
  - "時區 [.NET Framework], 還原序列化"
  - "時區 [.NET Framework], 還原"
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：從內嵌資源還原時區
本主題說明如何將儲存在資源檔案中的時區還原。  如需儲存時區的詳細資訊和指示，請參閱 [如何：將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)。  
  
### 從內嵌資源將 TimeZoneInfo 物件還原序列化  
  
1.  如果要擷取的時區不是自訂時區，請使用 <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> 方法嘗試將時區具現化。  
  
2.  將內嵌資源檔的完整名稱及參考傳送給內含資源檔的組件，將 <xref:System.Resources.ResourceManager> 物件具現化。  
  
     如果您無法判斷內嵌資源檔的完整名稱，請使用 [Ildasm.exe \(IL Disassembler\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 查看組件的資訊清單。  `.mresource` 項目會識別資源。  在本範例中，資源的完整名稱是 `SerializeTimeZoneData.SerializedTimeZones`。  
  
     如果資源檔內嵌在內含時區具現化程式碼的同一個組件中，您可以呼叫 `static` \(在 Visual Basic 中為 `Shared`\) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> 方法，以擷取它的參考。  
  
3.  如果呼叫 <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> 方法失敗，或如果要將自訂時區具現化，請使用 <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName> 方法以擷取內含序列化時區的字串。  
  
4.  呼叫 <xref:System.TimeZoneInfo.FromSerializedString%2A> 方法，將時區資料還原序列化。  
  
## 範例  
 下列範例會將儲存在內嵌 .NET XML 資源檔中的 <xref:System.TimeZoneInfo> 物件還原序列化。  
  
 [!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
 [!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]  
  
 本程式碼說明例外狀況處理，以確保應用程式所需的 <xref:System.TimeZoneInfo> 物件確實存在。  首先會使用<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> 方法以擷取登錄中的 <xref:System.TimeZoneInfo> 物件，將物件具現化。  如果無法具現化時區，程式碼會從內嵌資源檔中擷取時區。  
  
 因為自訂時區 \(使用 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 方法具現化的時區\) 並沒有儲存在登錄中，所以程式碼並沒有呼叫 <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> 以具現化「南極科學研究站」時區。  而是立即查看內嵌資源檔以擷取內含時區資料的字串，再呼叫 <xref:System.TimeZoneInfo.FromSerializedString%2A> 方法。  
  
## 編譯程式碼  
 這個範例需要：  
  
-   將 System.Windows.Forms.dll 的參考及 System.Core.dll 新增至專案。  
  
-   匯入下列命名空間：  
  
     [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
     [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]  
  
## 請參閱  
 [日期、時間和時區](../../../docs/standard/datetime/index.md)   
 [時區概觀](../../../docs/standard/datetime/time-zone-overview.md)   
 [如何：將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)