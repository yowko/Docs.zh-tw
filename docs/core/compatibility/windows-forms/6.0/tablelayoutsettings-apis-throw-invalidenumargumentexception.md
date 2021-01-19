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
# <a name="selected-tablelayoutsettings-properties-throw-invalidenumargumentexception"></a><span data-ttu-id="ba18d-103">選取的 TableLayoutSettings 屬性擲回 System.componentmodel.invalidenumargumentexception</span><span class="sxs-lookup"><span data-stu-id="ba18d-103">Selected TableLayoutSettings properties throw InvalidEnumArgumentException</span></span>

<span data-ttu-id="ba18d-104"><xref:System.Windows.Forms.TableLayoutSettings> <xref:System.ComponentModel.InvalidEnumArgumentException> 如果您嘗試指派的值不正確，則選取的屬性現在會擲回。</span><span class="sxs-lookup"><span data-stu-id="ba18d-104">Selected <xref:System.Windows.Forms.TableLayoutSettings> properties now throw an <xref:System.ComponentModel.InvalidEnumArgumentException> if you attempt to assign an incorrect value.</span></span>

## <a name="change-description"></a><span data-ttu-id="ba18d-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="ba18d-105">Change description</span></span>

<span data-ttu-id="ba18d-106">在先前的 .NET 版本中， <xref:System.ArgumentOutOfRangeException> 如果您嘗試指派的值不正確，這些屬性會擲回。</span><span class="sxs-lookup"><span data-stu-id="ba18d-106">In previous .NET versions, these properties throw an <xref:System.ArgumentOutOfRangeException> if you attempt to assign an incorrect value.</span></span> <span data-ttu-id="ba18d-107">從 .NET 6.0 開始，這些屬性 <xref:System.ComponentModel.InvalidEnumArgumentException> 在這種情況下會擲回。</span><span class="sxs-lookup"><span data-stu-id="ba18d-107">Starting in .NET 6.0, these properties throw an <xref:System.ComponentModel.InvalidEnumArgumentException> in such cases.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="ba18d-108">變更的原因</span><span class="sxs-lookup"><span data-stu-id="ba18d-108">Reason for change</span></span>

<span data-ttu-id="ba18d-109"><xref:System.ComponentModel.InvalidEnumArgumentException>在類似情況下，擲回與現有的 WINDOWS FORMS API 相同。</span><span class="sxs-lookup"><span data-stu-id="ba18d-109">Throwing <xref:System.ComponentModel.InvalidEnumArgumentException> is in line with the existing Windows Forms API in similar situations.</span></span> <span data-ttu-id="ba18d-110">擲回此例外狀況也可為開發人員提供更好的 debug 體驗。</span><span class="sxs-lookup"><span data-stu-id="ba18d-110">Throwing this exception also provides developers with a better debug experience.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="ba18d-111">引進的版本</span><span class="sxs-lookup"><span data-stu-id="ba18d-111">Version introduced</span></span>

<span data-ttu-id="ba18d-112">.NET 6。0</span><span class="sxs-lookup"><span data-stu-id="ba18d-112">.NET 6.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="ba18d-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ba18d-113">Recommended action</span></span>

- <span data-ttu-id="ba18d-114">更新程式碼以避免指派不正確的值。</span><span class="sxs-lookup"><span data-stu-id="ba18d-114">Update the code to prevent assigning incorrect values.</span></span>
- <span data-ttu-id="ba18d-115">如有必要，請 <xref:System.ComponentModel.InvalidEnumArgumentException> 在存取這些 api 時處理。</span><span class="sxs-lookup"><span data-stu-id="ba18d-115">If necessary, handle an <xref:System.ComponentModel.InvalidEnumArgumentException> when accessing these APIs.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="ba18d-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ba18d-116">Affected APIs</span></span>

<span data-ttu-id="ba18d-117">下表列出受影響的屬性：</span><span class="sxs-lookup"><span data-stu-id="ba18d-117">The following table lists the affected properties:</span></span>

| <span data-ttu-id="ba18d-118">屬性</span><span class="sxs-lookup"><span data-stu-id="ba18d-118">Property</span></span> | <span data-ttu-id="ba18d-119">版本已變更</span><span class="sxs-lookup"><span data-stu-id="ba18d-119">Version changed</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TableLayoutPanel.CellBorderStyle?displayProperty=fullName> | <span data-ttu-id="ba18d-120">Preview 1</span><span class="sxs-lookup"><span data-stu-id="ba18d-120">Preview 1</span></span> |
| <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle?displayProperty=fullName> | <span data-ttu-id="ba18d-121">Preview 1</span><span class="sxs-lookup"><span data-stu-id="ba18d-121">Preview 1</span></span> |

<!--

### Affected APIs

- `P:System.Windows.Forms.TableLayoutPanel.CellBorderStyle`
- `P:System.Windows.Forms.TableLayoutPanel.GrowStyle`

### Category

Windows Forms

-->
