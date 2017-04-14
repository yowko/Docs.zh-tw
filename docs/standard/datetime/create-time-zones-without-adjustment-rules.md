---
title: "如何：建立沒有調整規則的時區 | Microsoft Docs"
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
  - "調整規則 [.NET Framework]"
  - "時區 [.NET Framework], 調整規則"
  - "時區 [.NET Framework], 建立"
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：建立沒有調整規則的時區
特定系統可能基於以下原因，而沒有應用程式所需的精確的時區資訊：  
  
-   本機系統登錄中從未定義這個時區。  
  
-   時區的資料已被修改或從登錄中移除。  
  
-   這個時區存在，但是並沒有針對特定歷史期間之時區調整的精確資訊。  
  
 在這種情況下，您可以呼叫 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 方法以定義應用程式所需的時區。  您可以使用這個方法的多載，以建立包含或不含調整規則的時區。  如果該時區支援日光節約時間，您可以使用固定或浮動調整規則來定義調整方式 \(如需這些用語的定義，請參閱[時區概觀](../../../docs/standard/datetime/time-zone-overview.md)的＜時區用語＞一節\)。  
  
> [!IMPORTANT]
>  呼叫 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 方法所建立的自訂時區不會新增至登錄中。  只能透過 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 方法呼叫所傳回的物件參考才能存取。  
  
 本主題說明如何建立不含調整規則的時區。  如果要建立支援日光節約時間調整規則的時區，請參閱 [如何：建立有調整規則的時區](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).  
  
### 建立有調整規則的時區  
  
1.  定義時區的顯示名稱。  
  
     顯示名稱遵循相當程度的標準格式，其中時區的 Coordinated Universal Time \(UTC\) 位移會包含在括號中，後面接著識別時區的字串、該時區的一或多個城市，或是該時區的一或多個國家或地區。  
  
2.  定義時區的標準時間之名稱。  通常，這個字串也會當成時區的識別項使用。  
  
3.  如果您要使用和時區的標準名稱不同的識別項，請定義時區識別項。  
  
4.  將定義時區的 UTC 位移之 <xref:System.TimeSpan> 物件個體化。  時間較 UTC 晚的時區，位移值是正的。  時間較 UTC 早的時區，位移值是負的。  
  
5.  呼叫 <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=fullName> 方法，將新時區具現化。  
  
## 範例  
 下列範例會定義南極洲的茂森 \(Mawson\) 之自訂時區，這個時區沒有調整規則。  
  
 [!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
 [!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]  
  
 指派給 <xref:System.TimeZoneInfo.DisplayName%2A> 屬性的字串遵循標準的格式，其中，時區的 UTC 位移後面接著易讀的時區描述。  
  
## 編譯程式碼  
 這個範例需要：  
  
-   將 System.Core.dll 的參考加入至專案中。  
  
-   匯入下列命名空間：  
  
     [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
     [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]  
  
## 請參閱  
 [日期、時間和時區](../../../docs/standard/datetime/index.md)   
 [時區概觀](../../../docs/standard/datetime/time-zone-overview.md)   
 [如何：建立有調整規則的時區](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)