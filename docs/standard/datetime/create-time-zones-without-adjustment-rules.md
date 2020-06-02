---
title: 如何：建立沒有調整規則的時區
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
ms.openlocfilehash: 1d8aae1284e9ee9871c6f201c6a00e0b547f95fa
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278034"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a>如何：建立沒有調整規則的時區

應用程式所需的精確時區資訊可能因下列幾個原因而不存在於特定系統上：

- 本機系統的登錄中從未定義過時區。

- 已從登錄中修改或移除時區的相關資料。

- 時區存在，但沒有特定歷程記錄期間之時區調整的精確資訊。

在這些情況下，您可以呼叫 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 方法來定義應用程式所需的時區。 您可以使用這個方法的多載來建立具有或不含調整規則的時區。 如果時區支援日光節約時間，您可以使用固定或浮動調整規則來定義調整。 （如需這些詞彙的定義，請參閱時區[總覽](time-zone-overview.md)中的「時區詞彙」一節）。

> [!IMPORTANT]
> 藉由呼叫方法所建立的自訂時間區域 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 不會新增至登錄。 相反地，它們只能透過方法呼叫所傳回的物件參考來存取 <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> 。

本主題說明如何建立沒有調整規則的時區。 若要建立支援日光節約時間調整規則的時區，請參閱 how [to：建立具有調整規則的時區](create-time-zones-with-adjustment-rules.md)。

### <a name="to-create-a-time-zone-without-adjustment-rules"></a>建立沒有調整規則的時區

1. 定義時區的顯示名稱。

   顯示名稱遵循相當標準的格式，其中時區與國際標準時間（UTC）的位移會括在括弧中，後面接著識別時區的字串、時區中的一或多個城市，或時區中的一或多個國家或地區。

2. 定義時區標準時間的名稱。 通常，這個字串也會當做時區的識別碼使用。

3. 如果您想要使用與時區標準名稱不同的識別碼，請定義時區識別碼。

4. 具現化 <xref:System.TimeSpan> 物件，其定義時區與 UTC 的位移。 時間與 UTC 時間較晚的時區具有正位移。 具有早于 UTC 時間的時區具有負位移。

5. 呼叫 <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> 方法，以具現化新的時區。

## <a name="example"></a>範例

下列範例會定義茂遜，南極洲的自訂時區，此時區沒有調整規則。

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

指派給屬性的字串 <xref:System.TimeZoneInfo.DisplayName%2A> 會遵循標準格式，其中時區與 UTC 的位移後面會接著時區的易記描述。

## <a name="compiling-the-code"></a>編譯程式碼

這個範例需要：

- 匯入下列命名空間：

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a>另請參閱

- [日期、時間和時區](index.md)
- [時區總覽](time-zone-overview.md)
- [How to：建立具有調整規則的時區](create-time-zones-with-adjustment-rules.md)
