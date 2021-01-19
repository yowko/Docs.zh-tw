---
title: 重大變更：某些 TableLayoutSettings 屬性擲回 System.componentmodel.invalidenumargumentexception
description: 瞭解 .NET 6.0 中的重大變更，其中某些 TableLayoutSettings Api 現在會擲回無效引數的 System.componentmodel.invalidenumargumentexception。
ms.date: 01/18/2021
ms.openlocfilehash: 8397952e4647347718f11597a100c5d764e7186b
ms.sourcegitcommit: f8cd3ef517ee177c99feed944824c27d208cc0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2021
ms.locfileid: "98570263"
---
# <a name="selected-tablelayoutsettings-properties-throw-invalidenumargumentexception"></a>選取的 TableLayoutSettings 屬性擲回 System.componentmodel.invalidenumargumentexception

<xref:System.Windows.Forms.TableLayoutSettings> <xref:System.ComponentModel.InvalidEnumArgumentException> 如果您嘗試指派的值不正確，則選取的屬性現在會擲回。

## <a name="change-description"></a>變更描述

在先前的 .NET 版本中， <xref:System.ArgumentOutOfRangeException> 如果您嘗試指派的值不正確，這些屬性會擲回。 從 .NET 6.0 開始，這些屬性 <xref:System.ComponentModel.InvalidEnumArgumentException> 在這種情況下會擲回。

## <a name="reason-for-change"></a>變更的原因

<xref:System.ComponentModel.InvalidEnumArgumentException>在類似情況下，擲回與現有的 WINDOWS FORMS API 相同。 擲回此例外狀況也可為開發人員提供更好的 debug 體驗。

## <a name="version-introduced"></a>引進的版本

.NET 6。0

## <a name="recommended-action"></a>建議的動作

- 更新程式碼以避免指派不正確的值。
- 如有必要，請 <xref:System.ComponentModel.InvalidEnumArgumentException> 在存取這些 api 時處理。

## <a name="affected-apis"></a>受影響的 API

下表列出受影響的屬性：

| 屬性 | 版本已變更 |
|-|-|-|-|
| <xref:System.Windows.Forms.TableLayoutPanel.CellBorderStyle?displayProperty=fullName> | Preview 1 |
| <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle?displayProperty=fullName> | Preview 1 |

<!--

### Affected APIs

- `P:System.Windows.Forms.TableLayoutPanel.CellBorderStyle`
- `P:System.Windows.Forms.TableLayoutPanel.GrowStyle`

### Category

Windows Forms

-->
