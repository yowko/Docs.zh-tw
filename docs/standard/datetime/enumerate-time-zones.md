---
title: "如何： 列舉時區的電腦上"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], enumerating
- enumerating time zones [.NET Framework]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2318a42040388adfe327f9d0075754daa1aa22a6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>如何： 列舉時區的電腦上

若要順利處理指定的時區，需要可供系統使用之時區的相關資訊。 Windows XP 和 Windows Vista 作業系統會將此資訊儲存在登錄中。 不過，雖然全世界的時區總數很大，但是登錄只會包含其中一部分的資訊。 此外，登錄本身是內容很容易變成故意或意外變更的動態結構。 因此，應用程式無法永遠假設特定時區已定義且可在系統上使用。 許多使用時區資訊應用程式之應用程式的第一個步驟，為是否可在本機系統上使用必要時區，或將可從中選取的時區清單提供給使用者。 這需要應用程式列舉本機系統上所定義的時區。

> [!NOTE]
> 如果應用程式依賴的本機系統不可定義為特定時區存在，應用程式可以確保它存在序列化和還原序列化時區的相關資訊。 時區然後加入至清單控制項，可讓應用程式使用者選取它。 如需詳細資訊，請參閱[如何： 為內嵌的資源儲存時區](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)和[How to： 從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)。

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>列舉本機系統上展示的時區

1. 呼叫 <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> 方法。 方法會傳回泛型<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>集合<xref:System.TimeZoneInfo>物件。 集合中的項目會依照其<xref:System.TimeZoneInfo.DisplayName%2A>屬性。 例如: 

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. 列舉個別<xref:System.TimeZoneInfo>使用集合中的物件`foreach`迴圈 （在 C# 中) 或`For Each`...`Next` 迴圈 （在 Visual Basic 中)，並在每個物件上執行任何所需的處理。 例如，下列程式碼會列舉<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>集合<xref:System.TimeZoneInfo>物件中傳回的步驟 1，並列出在主控台上每個時區的顯示名稱。

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>若要對使用者顯示的本機系統上有時間區域清單

1. 呼叫 <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> 方法。 方法會傳回泛型<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>集合<xref:System.TimeZoneInfo>物件。

2. 指定在步驟 1 中傳回的集合`DataSource`屬性的 Windows form 或 ASP.NET 清單控制項。

3. 擷取<xref:System.TimeZoneInfo>使用者選取的物件。

此範例說明對 Windows 應用程式。

## <a name="example"></a>範例

此範例會啟動 Windows 應用程式會顯示在清單方塊中的系統上所定義的時區。 範例接著會顯示對話方塊，其中包含的值<xref:System.TimeZoneInfo.DisplayName%2A>使用者所選取的時區物件的屬性。

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

最清單控制項 (例如<xref:System.Windows.Forms.ListBox?displayProperty=nameWithType>或<xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType>控制項) 可讓您將集合的物件變數指派其`DataSource`屬性只要該集合會實作<xref:System.Collections.IEnumerable>介面。 (泛型<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>類別會這。)若要顯示個別的物件集合中，控制項會呼叫該物件`ToString`方法來擷取用來代表物件的字串。 如果是<xref:System.TimeZoneInfo>物件`ToString`方法會傳回<xref:System.TimeZoneInfo>物件的顯示名稱 (的值及其<xref:System.TimeZoneInfo.DisplayName%2A>屬性)。

> [!NOTE]
> 因為清單控制項呼叫物件的`ToString`方法，您可以指派的集合<xref:System.TimeZoneInfo>物件來控制，讓控制項顯示每個物件，有意義的名稱，並擷取<xref:System.TimeZoneInfo>使用者選取的物件。 這就不需要擷取集合中每個物件的字串，將字串指派給集合，接著指派給控制項的`DataSource`屬性，擷取使用者選取的字串，然後使用這個字串擷取物件它描述。 

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

* 對 system.core.dll 的參考無法加入至專案。

* 應該是匯入下列命名空間：

  <xref:System>（在 C# 程式碼）

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>另請參閱

[日期、 時間和時區](../../../docs/standard/datetime/index.md)
[How to： 將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
[How to： 從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
