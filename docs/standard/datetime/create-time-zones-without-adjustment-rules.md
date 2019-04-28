---
title: HOW TO：建立沒有調整規則的時區
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb3ffc7b6f1f7baec7ce6beb5a50b706ff78bfa1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026545"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>HOW TO：建立沒有調整規則的時區

應用程式所需的精確的時區資訊可能不存在特定的系統上有幾個原因：

* 永遠不會在本機系統登錄中定義時區。

* 已修改或從登錄中移除時區相關的資料。

* 時區存在，但並沒有特定的歷程記錄時間會調整時區的精確資訊。

在這些情況下，您可以呼叫<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法，以定義應用程式所需的時區。 您可以使用此方法的多載來建立時間的時區，或沒有調整規則。 如果時區支援日光節約時間，您可以定義其中一個固定或浮動調整規則的調整。 (如需這些詞彙的定義，請參閱 < 時區詞彙 > 一節[時區概觀](../../../docs/standard/datetime/time-zone-overview.md)。)

> [!IMPORTANT]
> 藉由呼叫建立的自訂時區<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法不會新增至登錄。 相反地，存取他們只能透過所傳回的物件參考<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法呼叫。

本主題說明如何建立沒有調整規則的時區。 若要建立支援日光節約時間調整規則的時區，請參閱[How to:建立有調整規則的時區](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)。

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>若要建立沒有調整規則的時區

1. 定義時區的顯示名稱。

   顯示名稱會遵循相當標準的格式 Coordinated Universal Time (UTC) 時區的位移以括弧括住且後面跟著識別時區，一或多個城市的時區，或其中一個或多個 cou 的字串ntries 或時區中的區域。

2. 定義時區標準時間的名稱。 一般而言，這個字串也做時區的識別項。

3. 如果您想要使用不同的識別碼，與時區的標準名稱，定義的時區識別項。

4. 具現化<xref:System.TimeSpan>定義與 UTC 的時區時差的物件。 時間會晚於 UTC 的時區有正面的位移。 與時間早於 UTC 的時區有負數位移。

5. 呼叫<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType>方法具現化新的時區。

## <a name="example"></a>範例

下列範例會定義茂遜，南極大陸，沒有調整規則的自訂時區。

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

將字串指派到<xref:System.TimeZoneInfo.DisplayName%2A>屬性會遵循標準格式與 UTC 的時區時差後面時區的好記的描述。

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

* 對 System.Core.dll 的參考加入至專案。

* 下列命名空間會匯入：

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>另請參閱

- [日期、時間和時區](../../../docs/standard/datetime/index.md)
- [時區概觀](../../../docs/standard/datetime/time-zone-overview.md)
- [如何：建立有調整規則的時區](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
