---
title: 如何： 建立沒有調整規則的時區
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
ms.openlocfilehash: 214e3bca811f87f4b8367b459564449d16e7c289
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>如何： 建立沒有調整規則的時區

為應用程式所需的精確的時區資訊可能不存在特定的系統上有幾個原因：

* 時區永遠不會在本機系統登錄中已定義。

* 已經修改或移除登錄中時區的相關資料。

* 時區存在，但並沒有特定的歷程記錄期間時區調整的正確資訊。

在這些情況下，您可以呼叫<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法，以定義應用程式所需的時區。 您可以使用這個方法的多載來建立具有或沒有調整規則的時區。 如果時區支援日光節約時間，您可以定義其中一個固定或浮動調整規則的調整。 (如需這些詞彙的定義，請參閱 < 時區詞彙 」 一節[時區概觀](../../../docs/standard/datetime/time-zone-overview.md)。)

> [!IMPORTANT]
> 藉由呼叫建立的自訂時區<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法不會加入至登錄。 相反地，他們可以只透過存取所傳回的物件參考<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>方法呼叫。

本主題示範如何建立沒有調整規則的時區。 若要建立支援日光節約時間調整規則的時區，請參閱[How to： 建立有調整規則的時區](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)。

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>若要建立沒有調整規則的時區

1. 定義時區的顯示名稱。

   顯示名稱會遵循國際標準時間 (UTC) 時區的位移加上括弧和後面的字串，識別時區，一或多個時區中，或其中一個城市的多個 cou 相當標準格式ntries 或時區中的區域。

2. 定義時區標準時間名稱。 一般而言，這個字串也做時區的識別項。

3. 如果您想要使用不同的識別項與時區的標準名稱，定義時區識別項。

4. 具現化<xref:System.TimeSpan>定義與 UTC 的時區時差的物件。 較晚於 UTC 的時區有正面的位移。 時間早於 UTC 的時區有了負數的位移。

5. 呼叫<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType>方法來具現化新的時區。

## <a name="example"></a>範例

下列範例會定義自訂的時區茂森，南極洲，沒有調整規則。

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

指派給字串<xref:System.TimeZoneInfo.DisplayName%2A>屬性會遵循標準格式與 UTC 的時區時差後面時區的好記的描述。

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

* 對 system.core.dll 的參考無法加入至專案。

* 應該是匯入下列命名空間：

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>另請參閱

[日期、 時間和時區](../../../docs/standard/datetime/index.md)
[時區概觀](../../../docs/standard/datetime/time-zone-overview.md)
[How to： 建立有調整規則的時區](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)
