---
title: "如何：列舉電腦上展示的時區"
description: "如何列舉電腦上展示的時區"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: c5ae4a6c-1790-4355-b5b1-879aaf956129
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: 5f385636137777013b540e8c1233751624139859

---

# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>如何：列舉電腦上展示的時區

若要順利處理指定的時區，需要可供系統使用之時區的相關資訊。 例如，Windows 作業系統會將此資訊儲存在登錄中。 不過，雖然全世界的時區總數很大，但是登錄只會包含其中一部分的資訊。 此外，登錄本身是內容很容易變成故意或意外變更的動態結構。 因此，應用程式無法永遠假設特定時區已定義且可在系統上使用。 許多使用時區資訊應用程式之應用程式的第一個步驟，為是否可在本機系統上使用必要時區，或將可從中選取的時區清單提供給使用者。 這需要應用程式列舉本機系統上所定義的時區。 

## <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>列舉本機系統上展示的時區

1. 呼叫 [TimeZoneInfo.GetSystemTimeZones](xref:System.TimeZoneInfo.GetSystemTimeZones) 方法。 這個方法會傳回 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件的泛型 [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) 集合。 集合中的項目會根據 [DisplayName](xref:System.TimeZoneInfo.DisplayName) 屬性進行排序。 例如: 

    ```csharp
    ReadOnlyCollection<TimeZoneInfo> tzCollection;
    tzCollection = TimeZoneInfo.GetSystemTimeZones();
    ```

    ```vb
    Dim tzCollection As ReadOnlyCollection(Of TimeZoneInfo) = TimeZoneInfo.GetSystemTimeZones
    ```

2. 使用 `foreach` 迴圈 (在 C# 中) 或 `For Each…Next` 迴圈 (在 Visual Basic 中) 來列舉集合中的個別 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件，並對每個物件執行任何必要的處理。 例如，下列程式碼會列舉步驟 1 中所傳回之 [TimeZoneInfo](xref:System.TimeZoneInfo) 物件的 [ReadOnlyCollection&lt;T&gt;](xref:System.Collections.ObjectModel.ReadOnlyCollection%601) 集合，並在主控台上列出每個時區的顯示名稱。

    ```csharp
    foreach (TimeZoneInfo timeZone in tzCollection)
    Console.WriteLine("   {0}: {1}", timeZone.Id, timeZone.DisplayName);
    ```

    ```vb
    For Each timeZone As TimeZoneInfo In tzCollection
        Console.WriteLine("   {0}: {1}", timeZone.Id, timeZone.DisplayName)
    Next
    ```

## <a name="see-also"></a>另請參閱

[日期、時間及時區](index.md)

[尋找本機系統上定義的時區](finding-the-time-zones-on-local-system.md)




<!--HONumber=Nov16_HO3-->


