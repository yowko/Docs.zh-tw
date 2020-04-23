---
title: x:Members 指示詞
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: c751a4f1cdea8dce7ef5165f5225ab3a825c7344
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071462"
---
# <a name="xmembers-directive"></a>x:Members 指示詞
保存在標記中定義的一組成員,該成員適用於父元素的 x:類。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<object x:Class="className">
<x:Members>
  oneOrMoreMembers
</x:Members
</object>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`className`|XAML 生產的支援類別或部分類別名稱。 請參閱＜備註＞。|
|`oneOrMoreMembers`|表示成員定義的一個或多個物件元素。 通常,這些是`x:Property`物件元素。 請參閱＜備註＞。|

## <a name="remarks"></a>備註

在 .NET XAML 服務實現中`x:Members`,沒有支援類或基礎成員實現。 `x:Members`是可作為任何類型的成員存在的特殊 XAML 成員。 在 XAML`x:Members`節點流 中,從 XAML 語言 XAML 命名空間中表示為名為`Members`的成員。 該成員`Members``Member`包含 物件的唯讀泛型清單。 在典型的標記中,單個成員被指定為`x:Property`屬性元素。 `x:Property`是專門針對類型屬性的更精確的類型,可分配給`x:Member`。 有關詳細資訊,請參閱[x:屬性指令](xproperty-directive.md)。

若要支援實際使用 `x:Members` 做為在標記中指定成員定義的方法，這些成員必須與可修改的類別相關聯。 預期的模型是 `x:Members` 做為可指定 `x:Class` 之類型成員的形式存在。 但是,在 .NET XAML 服務級別不支援關聯類型和成員或生成動態成員定義的機制。 這會保留給具有支援 XAML 成員定義之應用程式模型的個別架構。 通常需要 MSBUILD 建置動作以標記編譯 XAML，然後與程式碼後置整合，或是從 XAML 產生純組件，才能支援該功能。

## <a name="xmembers-for-windows-workflow-foundation"></a>X:Windows 工作流基礎的成員

對於 Windows`x:Members`工作流基礎,包含完全以 XAML 或 XAML — 定義具有代碼後面的活動設計器的動態成員組成的自定義活動的成員。 `x:Class` 也必須在 XAML 生產的根項目上指定。 這不是 .NET XAML 服務級別的要求,但當支援自定義活動和 Windows 工作流基礎 XAML 的 MSBUILD 生成操作載入 XAML 生產時,這將成為一項要求。 `x:Members`必須是宣告的物件元素標記中的第一個子元素`x:Class`。
