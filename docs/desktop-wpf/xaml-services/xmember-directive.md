---
title: x:Member 指示詞
ms.date: 03/30/2017
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
ms.openlocfilehash: e82bb6397404ee466a12ab438585ae1898c34d1a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071469"
---
# <a name="xmember-directive"></a>x:Member 指示詞
在標記中宣告 XAML 成員。

## <a name="xaml-object-element-usage"></a>XAML 物件項目用法

```xaml
<object x:Class="className">
  <x:Members>
    <x:Member Name="propertyName"/>
    additionalMembers
  </x:Members>
</object>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`className`|XAML 生產的支援類別或部分類別名稱。|
|`memberName`|正在定義之屬性的成員名稱。|

## <a name="remarks"></a>備註

在 .NET XAML 服務實現中, `x:Member` 沒有直接的類型支援，但受到 <xref:System.Windows.Markup.MemberDefinition> 類別的支援。 在 XAML 節點資料流中，`x:Member` 項目會以 XAML 語言 XAML 命名空間中名為 `Member` 的成員表示。 成員 `Member` 包含以標記宣告的屬性。

的表示義`Name``Type`不在 .NET XAML 服務級別分配。 它們會在初始 XAML 節點資料流中儲存為字串值，以便稍後依據特定架構可能加諸的規則解譯。 這個意義可能與 XAML 名稱和 XAML 類型的意義一致，或可能只是在支援類型系統中有效，視實作而定。

若要支援實際使用 `x:Members` 做為在標記中指定成員定義的方法，這些成員必須與可修改的類別相關聯。 預期的模型是 `x:Members` 做為可指定 `x:Class` 之類型成員的形式存在。 但是,在 .NET XAML 服務級別不支援關聯類型和成員或生成動態成員定義的機制。 這會保留給具有支援 XAML 成員定義之應用程式模型的個別架構。 通常需要 MSBUILD 建置動作以標記編譯 XAML，然後與程式碼後置整合，或是從 XAML 產生純組件，才能支援該功能。

## <a name="xproperty-for-windows-workflow-foundation"></a>Windows Workflow Foundation 的 x:Property

針對 Windows Workflow Foundation，`x:Property` 會定義完全以 XAML 撰寫之自訂活動的成員，或程式碼後置活動設計工具的 XAML 定義動態成員。 `x:Class` 也必須在 XAML 生產的根項目上指定。 這不是 .NET XAML 服務級別的要求,但當支援自定義活動和 Windows 工作流基礎 XAML 的 MSBUILD 生成操作載入 XAML 生產時,這將成為一項要求。 Windows 工作流基礎不使用純 XAML 類型`x:Property``Type`名稱作為其 屬性的預期值,而是使用此處未記錄的約定。 有關詳細資訊,請參閱[動態活動建立](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100))。
