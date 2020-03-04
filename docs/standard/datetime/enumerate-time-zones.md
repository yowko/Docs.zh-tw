---
title: 如何：列舉電腦上存在的時區
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], enumerating
- enumerating time zones [.NET Framework]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
ms.openlocfilehash: aa8962c8aea208778983610041937dc3f75c1f1e
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159438"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>如何：列舉電腦上存在的時區

若要順利處理指定的時區，需要可供系統使用之時區的相關資訊。 Windows XP 和 Windows Vista 作業系統會將這項資訊儲存在登錄中。 不過，雖然全世界的時區總數很大，但是登錄只會包含其中一部分的資訊。 此外，登錄本身是內容很容易變成故意或意外變更的動態結構。 因此，應用程式無法永遠假設特定時區已定義且可在系統上使用。 許多使用時區資訊應用程式之應用程式的第一個步驟，為是否可在本機系統上使用必要時區，或將可從中選取的時區清單提供給使用者。 這需要應用程式列舉本機系統上所定義的時區。

> [!NOTE]
> 如果應用程式依賴本機系統上可能未定義的特定時區存在，應用程式可以藉由序列化和還原序列化時區的相關資訊，確保其存在。 接著，您可以將時區加入清單控制項，讓應用程式使用者可以選取它。 如需詳細資訊，請參閱[如何：將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)和[如何：從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)。

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>列舉本機系統上展示的時區

1. 呼叫 <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> 方法。 方法會傳回 <xref:System.TimeZoneInfo> 物件的泛型 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 集合。 集合中的專案會依其 <xref:System.TimeZoneInfo.DisplayName%2A> 屬性進行排序。 例如：

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. 使用 `foreach` 迴圈（在中C#）或 `For Each`... 來列舉集合中的個別 <xref:System.TimeZoneInfo> 物件`Next` 迴圈（在 Visual Basic 中），並在每個物件上執行任何必要的處理。 例如，下列程式碼會列舉步驟1中所傳回 <xref:System.TimeZoneInfo> 物件的 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 集合，並列出主控台上每個時區的顯示名稱。

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>向使用者呈現本機系統上的時區清單

1. 呼叫 <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> 方法。 方法會傳回 <xref:System.TimeZoneInfo> 物件的泛型 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 集合。

2. 將步驟1中傳回的集合指派給 Windows forms 或 ASP.NET 清單控制項的 `DataSource` 屬性。

3. 取出使用者已選取的 <xref:System.TimeZoneInfo> 物件。

此範例會提供 Windows 應用程式的說明。

## <a name="example"></a>範例

此範例會啟動 Windows 應用程式，以在清單方塊中顯示系統上定義的時區。 然後，此範例會顯示一個對話方塊，其中包含使用者選取之時區物件的 <xref:System.TimeZoneInfo.DisplayName%2A> 屬性值。

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

大部分的清單控制項（例如 <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> 或 <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> 控制項）可讓您將物件變數的集合指派給其 `DataSource` 屬性，前提是該集合會執行 <xref:System.Collections.IEnumerable> 介面。 （泛型 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> 類別會執行此工作）。若要在集合中顯示個別物件，控制項會呼叫該物件的 `ToString` 方法，以解壓縮用來表示物件的字串。 在 <xref:System.TimeZoneInfo> 物件的情況下，`ToString` 方法會傳回 <xref:System.TimeZoneInfo> 物件的顯示名稱（其 <xref:System.TimeZoneInfo.DisplayName%2A> 屬性的值）。

> [!NOTE]
> 因為清單控制項會呼叫物件的 `ToString` 方法，所以您可以將 <xref:System.TimeZoneInfo> 物件的集合指派給控制項，讓控制項為每個物件顯示有意義的名稱，並取出使用者已選取的 <xref:System.TimeZoneInfo> 物件。 這樣就不需要將集合中每個物件的字串解壓縮，將字串指派給指派給控制項之 `DataSource` 屬性的集合，並抓取使用者所選取的字串，然後使用這個字串來解壓縮它所描述的物件。

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

- 匯入下列命名空間：

  <xref:System> （在C#程式碼中）

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>另請參閱

- [日期、時間及時區](../../../docs/standard/datetime/index.md)
- [操作說明：將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
- [操作說明：從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
