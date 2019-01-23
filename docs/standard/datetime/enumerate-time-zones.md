---
title: HOW TO：列舉電腦上展示的時區
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], enumerating
- enumerating time zones [.NET Framework]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 697cd40482aee73fd150359acb710ffc258c3df2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518406"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>HOW TO：列舉電腦上展示的時區

若要順利處理指定的時區，需要可供系統使用之時區的相關資訊。 Windows XP 和 Windows Vista 作業系統會將此資訊儲存在登錄中。 不過，雖然全世界的時區總數很大，但是登錄只會包含其中一部分的資訊。 此外，登錄本身是內容很容易變成故意或意外變更的動態結構。 因此，應用程式無法永遠假設特定時區已定義且可在系統上使用。 許多使用時區資訊應用程式之應用程式的第一個步驟，為是否可在本機系統上使用必要時區，或將可從中選取的時區清單提供給使用者。 這需要應用程式列舉本機系統上所定義的時區。

> [!NOTE]
> 如果應用程式依賴本機系統可能沒有定義為特定時區的目前狀態，應用程式可以確保其目前狀態序列化和還原序列化的相關時區資訊。 時區然後新增到清單控制項，使應用程式使用者可以選取它。 如需詳細資訊，請參閱[How to:將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)和[How to:從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)。

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>列舉本機系統上展示的時區

1. 呼叫 <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> 方法。 此方法會傳回泛型<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>的集合<xref:System.TimeZoneInfo>物件。 集合中的項目會依其<xref:System.TimeZoneInfo.DisplayName%2A>屬性。 例如: 

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. 列舉個別<xref:System.TimeZoneInfo>使用集合中的物件`foreach`迴圈 （在 C#) 或`For Each`...`Next` 迴圈 （在 Visual Basic 中)，並在每個物件上執行任何必要的處理。 例如，下列程式碼會列舉<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>的集合<xref:System.TimeZoneInfo>物件傳回在步驟 1，並列出在主控台上的每個時區的顯示名稱。

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>若要顯示給使用者的本機系統上展示的時區清單

1. 呼叫 <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> 方法。 此方法會傳回泛型<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>的集合<xref:System.TimeZoneInfo>物件。

2. 將指定在步驟 1 中傳回的集合`DataSource`屬性的 Windows form 或 ASP.NET 清單控制項。

3. 擷取<xref:System.TimeZoneInfo>使用者選取的物件。

此範例說明針對 Windows 應用程式。

## <a name="example"></a>範例

此範例會啟動 Windows 應用程式會顯示在清單方塊中的系統上所定義的時區。 此範例接著會顯示對話方塊，其中包含的值<xref:System.TimeZoneInfo.DisplayName%2A>使用者所選取的時區物件的屬性。

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

最清單控制項 (例如<xref:System.Windows.Forms.ListBox?displayProperty=nameWithType>或<xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType>控制項) 可讓您指派至的物件變數的集合及其`DataSource`屬性，只要該集合會實作<xref:System.Collections.IEnumerable>介面。 (泛型<xref:System.Collections.ObjectModel.ReadOnlyCollection%601>類別的做法。)若要顯示的個別物件在集合中，控制項會呼叫該物件的`ToString`方法來擷取用來代表物件的字串。 若是<xref:System.TimeZoneInfo>物件，`ToString`方法會傳回<xref:System.TimeZoneInfo>物件的顯示名稱 (的值及其<xref:System.TimeZoneInfo.DisplayName%2A>屬性)。

> [!NOTE]
> 因為清單控制項呼叫的物件`ToString`方法中，您可以將指派的集合<xref:System.TimeZoneInfo>物件來控制，讓控制項顯示有意義的名稱，每一個物件，並擷取<xref:System.TimeZoneInfo>使用者選取的物件。 這就不需要擷取集合中每個物件的字串，將字串指派給集合，其中依序指派給控制項的`DataSource`屬性，擷取使用者已選取的字串，然後使用此字串擷取物件它描述。 

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

* 對 System.Core.dll 的參考加入至專案。

* 下列命名空間會匯入：

  <xref:System> （在 C# 程式碼）

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>另請參閱

- [日期、時間和時區](../../../docs/standard/datetime/index.md)
- [如何：將時區儲存到內嵌資源](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
- [如何：從內嵌資源還原時區](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
