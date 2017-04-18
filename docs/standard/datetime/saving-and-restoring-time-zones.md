---
title: "儲存和還原時區 | Microsoft Docs"
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
  - "還原序列化 [.NET Framework], 時區"
  - "還原時區"
  - "儲存時區"
  - "序列化 [.NET Framework], 時區"
  - "時區物件 [.NET Framework], 還原序列化"
  - "時區物件 [.NET Framework], 還原"
  - "時區物件 [.NET Framework], 儲存"
  - "時區物件 [.NET Framework], 序列化"
  - "時區 [.NET Framework], 還原"
  - "時區 [.NET Framework], 儲存"
ms.assetid: 4028b310-e7ce-49d4-a646-1e83bfaf6f9d
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 儲存和還原時區
<xref:System.TimeZoneInfo> 類別必須藉助登錄才能擷取預先定義的時區資料。  但是，登錄是一種動態結構。  此外，登錄中內含的時區資訊，主要是由作業系統用來處理當年度的時間調整及轉換。  這麼做對於必須藉助時區資料的應用程式而言，有兩個重要的含意：  
  
-   應用程式所需的時區可能未定義在登錄中，或已重新命名或從登錄中移除。  
  
-   登錄中所定義的時區可能缺少特定調整規則的資訊，而這些是進行歷史時區轉換時必要的資訊。  
  
 <xref:System.TimeZoneInfo> 類別經由支援序列化 \(儲存\) 及還原序列化 \(還原\) 時區資料，以解決這個限制。  
  
## 時區序列化及還原序列化  
 以序列化和還原序列化時區資料的方式儲存及還原時區，需要兩個方法呼叫：  
  
-   您可以呼叫物件的 <xref:System.TimeZoneInfo.ToSerializedString%2A> 方法，將 <xref:System.TimeZoneInfo> 物件序列化。  這個方法不使用參數，並會傳回內含時區資訊的字串。  
  
-   將已序列化的字串傳送給 `static` \(在 Visual Basic 中為`Shared` \) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=fullName> 方法，就可以從字串中將 <xref:System.TimeZoneInfo> 物件還原序列化。  
  
## 序列化及還原序列化的情形  
 將 <xref:System.TimeZoneInfo> 物件儲存 \(序列化\) 成字串，以及還原 \(還原序列化\) 以供日後使用，可以提高 <xref:System.TimeZoneInfo> 類別的實用性及彈性。  本節將詳細說明幾個最適用序列化及還原序列化的情形。  
  
### 序列化及還原序列化應用程式中的時區資料  
 當有需要時，可以從字串還原已序列化的時區。  如果擷取自登錄的時區無法正確轉換特定日期範圍內的日期與時間，應用程式就可能會這麼做。  例如，Windows XP 登錄中的時區資料支援單一調整規則，而 Windows Vista 登錄中所定義的時區則提供兩種調整規則的資訊。  這表示歷史時間轉換可能不精確。  而序列化和還原序列化時區資料可以解決這個限制。  
  
 在下列範例中，沒有調整規則的自訂 <xref:System.TimeZoneInfo> 類別會定義為代表從 1883 到 1917，日光節約時間推行之前的美國東部標準時間。  自訂的時區會序列化成全域範圍的變數。  時區轉換方法 \(`ConvertUtcTime`\) 會傳送給 Coordinated Universal Time \(UTC\) 時間以進行轉換。  如果日期與時間發生在 1917 年或更早，自訂的「東部標準時間」區就會從已序列化的字串還原，並取代從登錄中擷取的時區。  
  
 [!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
 [!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]  
  
### 處理時區例外狀況  
 因為登錄是一種動態結構，所以內容會受到意外或刻意變更而改變。  也就是說，登錄中應該要定義才能使應用程式順利執行的時區，可能並不存在。  如果沒有時區序列化及還原序列化支援，您就只能結束應用程式才能處理產生的 <xref:System.TimeZoneNotFoundException> 結果。  但是，您可以使用時區序列化及還原序列化的方式，將所需的時區從序列化字串還原以處理非預期的 <xref:System.TimeZoneNotFoundException>，應用程式就能繼續執行。  
  
 下列範例會建立並序列化自訂的「中央標準時間」區。  然後嘗試擷取登錄中的「中央標準時間」區。  如果擷取作業擲回 <xref:System.TimeZoneNotFoundException> 或 <xref:System.InvalidTimeZoneException>，例外狀況處理常式就會還原序列化時區。  
  
 [!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
 [!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]  
  
### 需要時儲存已序列化的字串及還原  
 上一個範例將時區資訊儲存成字串變數，並在需要時還原。  但是內含序列化時區資訊的字串可以儲存在儲存媒體中，例如外部檔案、應用程式內嵌的資源檔，或是登錄中 \(請注意，自訂時區資訊應該要和登錄中的系統時區索引鍵分開儲存\)。  
  
 以這個方式儲存序列化時區字串，也會將時區建立常式和應用程式分開。  例如，時區建立常式也可以執行和建立資料檔，內含應用程式可使用的歷史時區資訊。  資料檔就可以和應用程式一起安裝，當應用程式需要時就可以開啟、還原序列化一或多個時區。  
  
 如需使用內嵌資源以儲存序列化時區資料的詳細資訊，請參閱 [如何：將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)及 [如何：從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)。  
  
## 請參閱  
 [日期、時間和時區](../../../docs/standard/datetime/index.md)