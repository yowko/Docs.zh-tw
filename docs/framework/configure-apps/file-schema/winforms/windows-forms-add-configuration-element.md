---
title: "Windows Form 加入組態項目"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 367ca30c577cbb4ed7fed130bdcbd4faac2d46c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="windows-forms-add-configuration-element"></a><span data-ttu-id="fc7a9-102">Windows Form 加入組態項目</span><span class="sxs-lookup"><span data-stu-id="fc7a9-102">Windows Forms Add Configuration Element</span></span>

<span data-ttu-id="fc7a9-103">`<add>`項目加入預先定義的索引鍵，指定您的 Windows Form 應用程式是否支援加入.NET Framework 4.7 在或更新版本的 Windows Forms 應用程式的功能。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-103">The `<add>` element adds a predefined key that specifies whether your Windows Form app supports features added to Windows Forms apps in the .NET Framework 4.7 or later.</span></span>

## <a name="syntax"></a><span data-ttu-id="fc7a9-104">語法</span><span class="sxs-lookup"><span data-stu-id="fc7a9-104">Syntax</span></span>

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="key-name" value="key-value" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fc7a9-105">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="fc7a9-105">Attributes and elements</span></span>

<span data-ttu-id="fc7a9-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="fc7a9-107">屬性</span><span class="sxs-lookup"><span data-stu-id="fc7a9-107">Attributes</span></span>

| <span data-ttu-id="fc7a9-108">屬性</span><span class="sxs-lookup"><span data-stu-id="fc7a9-108">Attribute</span></span> | <span data-ttu-id="fc7a9-109">描述</span><span class="sxs-lookup"><span data-stu-id="fc7a9-109">Description</span></span> |
| --------- | ----------- |
| `key`     | <span data-ttu-id="fc7a9-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-110">Required attribute.</span></span> <span data-ttu-id="fc7a9-111">預先定義的索引鍵名稱對應至特定的 Windows Form 可自訂功能。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-111">A predefined key name that corresponds to a particular Windows Forms customizable feature.</span></span> |
| `value`   | <span data-ttu-id="fc7a9-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-112">Required attribute.</span></span> <span data-ttu-id="fc7a9-113">要指派給值`key`。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-113">The value to assign to `key`.</span></span> |

### <a name="key-attribute-names-and-associated-values"></a><span data-ttu-id="fc7a9-114">`key`屬性名稱和相關聯的值</span><span class="sxs-lookup"><span data-stu-id="fc7a9-114">`key` attribute names and associated values</span></span>

| <span data-ttu-id="fc7a9-115">`key` 名稱</span><span class="sxs-lookup"><span data-stu-id="fc7a9-115">`key` name</span></span> | <span data-ttu-id="fc7a9-116">值</span><span class="sxs-lookup"><span data-stu-id="fc7a9-116">Values</span></span> | <span data-ttu-id="fc7a9-117">說明</span><span class="sxs-lookup"><span data-stu-id="fc7a9-117">Description</span></span> |
| ---------- | ------ | ----------- |
| <span data-ttu-id="fc7a9-118">「 AnchorLayout.DisableSinglePassControlScaling"</span><span class="sxs-lookup"><span data-stu-id="fc7a9-118">"AnchorLayout.DisableSinglePassControlScaling"</span></span> | <span data-ttu-id="fc7a9-119">"true"&#124;"false"</span><span class="sxs-lookup"><span data-stu-id="fc7a9-119">"true"&#124;"false"</span></span> | <span data-ttu-id="fc7a9-120">指出是否錨定的控制項在單一行程中縮放。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-120">Indicates whether anchored controls are scaled in a single pass.</span></span> <span data-ttu-id="fc7a9-121">若要停用單一"true"傳遞縮放比例。否則為 false。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-121">"true" to disable single pass scaling; otherwise, false.</span></span> <span data-ttu-id="fc7a9-122">請參閱中的 「 單一傳遞調整 」 一節[備註](#Remarks)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-122">See the "Single pass scaling" section in the [Remarks](#Remarks) for more information.</span></span> |
| <span data-ttu-id="fc7a9-123">「 DpiAwareness"</span><span class="sxs-lookup"><span data-stu-id="fc7a9-123">"DpiAwareness"</span></span> | <span data-ttu-id="fc7a9-124">「 PerMonitorV2"&#124;"false"</span><span class="sxs-lookup"><span data-stu-id="fc7a9-124">"PerMonitorV2"&#124;"false"</span></span> | <span data-ttu-id="fc7a9-125">指出是否為 DPI 感知應用程式。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-125">Indicates whether an application is DPI-aware.</span></span> <span data-ttu-id="fc7a9-126">設定"PerMonitorV2 」 支援 Dpi 感知; 的索引鍵否則，將它設定為"false"。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-126">Set the key to "PerMonitorV2" to support Dpi awareness; otherwise, set it to "false".</span></span> <span data-ttu-id="fc7a9-127">DPI 感知是選擇性功能。若要利用 Windows Form 高 DPI 支援，您應該將其值設"PerMonitorV2"。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-127">DPI awareness is an opt-in feature; to take advantage of Windows Forms' high DPI support, you should set its value to "PerMonitorV2".</span></span> <span data-ttu-id="fc7a9-128">請參閱[備註](#remarks)節的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-128">See the [Remarks](#remarks) section for more information.</span></span> |
| <span data-ttu-id="fc7a9-129">「 CheckedListBox.DisableHighDpiImprovements"</span><span class="sxs-lookup"><span data-stu-id="fc7a9-129">"CheckedListBox.DisableHighDpiImprovements"</span></span> | <span data-ttu-id="fc7a9-130">"true"&#124;"false"</span><span class="sxs-lookup"><span data-stu-id="fc7a9-130">"true"&#124;"false"</span></span> | <span data-ttu-id="fc7a9-131">指出是否<xref:System.Windows.Forms.CheckedListBox>控制項利用.NET Framework 4.7 中導入的縮放比例和配置增強功能。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-131">Indicates whether the <xref:System.Windows.Forms.CheckedListBox> control takes advantage of scaling and layout improvements introduced in the .NET Framework 4.7.</span></span> <span data-ttu-id="fc7a9-132">"true"退出 caling 和配置的增強功能;否則，"false"。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-132">"true" to opt out of caling and layout improvements; otherwise, "false".</span></span> |
| <span data-ttu-id="fc7a9-133">「 DataGridView.DisableHighDpiImprovements"</span><span class="sxs-lookup"><span data-stu-id="fc7a9-133">"DataGridView.DisableHighDpiImprovements"</span></span> | <span data-ttu-id="fc7a9-134">"true"&#124;"false"</span><span class="sxs-lookup"><span data-stu-id="fc7a9-134">"true"&#124;"false"</span></span> | <span data-ttu-id="fc7a9-135">指出是否<xref:System.Windows.Forms.DataGridView>控制.NET Framework 4.7 中導入的縮放比例和配置增強功能。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-135">Indicates whether the <xref:System.Windows.Forms.DataGridView> control scaling and layout improvements introduced in the .NET Framework 4.7.</span></span> <span data-ttu-id="fc7a9-136">"true"退出 DPI 感知;"false"否則。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-136">"true" to opt out of DPI awareness; "false" otherwise.</span></span> |
| <span data-ttu-id="fc7a9-137">「 DisableDpiChangedMessageHandling"</span><span class="sxs-lookup"><span data-stu-id="fc7a9-137">"DisableDpiChangedMessageHandling"</span></span> | <span data-ttu-id="fc7a9-138">"true"&#124;"false"</span><span class="sxs-lookup"><span data-stu-id="fc7a9-138">"true"&#124;"false"</span></span> | <span data-ttu-id="fc7a9-139">"true"退出接收 DPI 縮放比例; 的變更與相關的訊息"false"否則。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-139">"true" to opt out of receiving messages related to DPI scaling changes; "false" otherwise.</span></span> <span data-ttu-id="fc7a9-140">請參閱[備註](#remarks)節的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-140">See the [Remarks](#remarks) section for more information.</span></span> |
| <span data-ttu-id="fc7a9-141">「 EnableWindowsFormsHighDpiAutoResizing"</span><span class="sxs-lookup"><span data-stu-id="fc7a9-141">"EnableWindowsFormsHighDpiAutoResizing"</span></span> | <span data-ttu-id="fc7a9-142">"true"&#124;"false"</span><span class="sxs-lookup"><span data-stu-id="fc7a9-142">"true"&#124;"false"</span></span> | <span data-ttu-id="fc7a9-143">表示在 Windows Forms 應用程式會自動調整大小因為 DPI 縮放比例變更。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-143">Indicates whether a Windows Forms application is automatically resized due to DPI scaling changes.</span></span> <span data-ttu-id="fc7a9-144">若要啟用自動調整大小;"true"否則為 false。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-144">"true" to enable automatic resizing; otherwise, false.</span></span> |
| <span data-ttu-id="fc7a9-145">「 Form.DisableSinglePassControlScaling"</span><span class="sxs-lookup"><span data-stu-id="fc7a9-145">"Form.DisableSinglePassControlScaling"</span></span> | <span data-ttu-id="fc7a9-146">"true"&#124;"false"</span><span class="sxs-lookup"><span data-stu-id="fc7a9-146">"true"&#124;"false"</span></span> | <span data-ttu-id="fc7a9-147">指出是否<xref:System.Windows.Forms.Form>調整在單一行程中。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-147">Indicates whether the <xref:System.Windows.Forms.Form> is scaled in a single pass.</span></span> <span data-ttu-id="fc7a9-148">縮放比例;"true"停用單一行程否則為 false。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-148">"true" to disable single-pass scaling; otherwise, false.</span></span> <span data-ttu-id="fc7a9-149">請參閱中的 「 單一傳遞調整 」 一節[備註](#Remarks)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-149">See the "Single pass scaling" section in the [Remarks](#Remarks) for more information.</span></span> |
| <span data-ttu-id="fc7a9-150">「 MonthCalendar.DisableSinglePassControlScaling"</span><span class="sxs-lookup"><span data-stu-id="fc7a9-150">"MonthCalendar.DisableSinglePassControlScaling"</span></span> | <span data-ttu-id="fc7a9-151">"true"&#124;"false"</span><span class="sxs-lookup"><span data-stu-id="fc7a9-151">"true"&#124;"false"</span></span> | <span data-ttu-id="fc7a9-152">指出是否<xref:System.Windows.Forms.MonthCalendar>在單一行程中縮放控制項。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-152">Indicates whether the <xref:System.Windows.Forms.MonthCalendar> control is scaled in a single pass.</span></span> <span data-ttu-id="fc7a9-153">縮放比例;"true"停用單一行程否則為 false。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-153">"true" to disable single-pass scaling; otherwise, false.</span></span> <span data-ttu-id="fc7a9-154">請參閱中的 「 單一傳遞調整 」 一節[備註](#Remarks)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-154">See the "Single pass scaling" section in the [Remarks](#Remarks) for more information.</span></span> |
| <span data-ttu-id="fc7a9-155">「 Toolstrip.DisableHighDpiImprovements"</span><span class="sxs-lookup"><span data-stu-id="fc7a9-155">"Toolstrip.DisableHighDpiImprovements"</span></span> | <span data-ttu-id="fc7a9-156">"true"&#124;"false"</span><span class="sxs-lookup"><span data-stu-id="fc7a9-156">"true"&#124;"false"</span></span> | <span data-ttu-id="fc7a9-157">指出是否<xref:System.Windows.Forms.ToolStrip>控制項利用.NET Framework 4.7 中導入的縮放比例和配置增強功能。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-157">Indicates whether the <xref:System.Windows.Forms.ToolStrip> control takes advantage of scaling and layout improvements introduced in the .NET Framework 4.7.</span></span> <span data-ttu-id="fc7a9-158">"true"退出 DPI 感知;"false"否則。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-158">"true" to opt out of DPI awareness; "false" otherwise.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="fc7a9-159">子元素</span><span class="sxs-lookup"><span data-stu-id="fc7a9-159">Child elements</span></span>

<span data-ttu-id="fc7a9-160">無。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-160">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fc7a9-161">父元素</span><span class="sxs-lookup"><span data-stu-id="fc7a9-161">Parent elements</span></span>

| <span data-ttu-id="fc7a9-162">元素</span><span class="sxs-lookup"><span data-stu-id="fc7a9-162">Element</span></span> | <span data-ttu-id="fc7a9-163">說明</span><span class="sxs-lookup"><span data-stu-id="fc7a9-163">Description</span></span> |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md) | <span data-ttu-id="fc7a9-164">設定新的 Windows Form 應用程式功能的支援。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-164">Configures support for new Windows Forms application features.</span></span> |

## <a name="a-nameremarks--remarks"></a><span data-ttu-id="fc7a9-165"><a name="remarks" />註解</span><span class="sxs-lookup"><span data-stu-id="fc7a9-165"><a name="remarks" /> Remarks</span></span>

<span data-ttu-id="fc7a9-166">從 .NET Framework 4.7 開始，`<System.Windows.Forms.ApplicationConfigurationSection>` 元素能允許您設定 Windows Forms 應用程式，以利用 .NET Framework 最新版本中的新增功能。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-166">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span> 

<span data-ttu-id="fc7a9-167">`<System.Windows.Forms.ApplicationConfigurationSection>`元素可讓您新增一個以上的子系`<add>`項目，其中每個定義特定的組態設定。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-167">The `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to add one or more child `<add>` elements, each of which defines a specific configuration setting.</span></span>  

<span data-ttu-id="fc7a9-168">如需 Windows Form 高 DPI 支援的概觀，請參閱[Windows Form 中的高 DPI 支援](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-168">For an overview of Windows Forms High DPI support, see [High DPI Support in Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).</span></span>

### <a name="dpiawareness"></a><span data-ttu-id="fc7a9-169">DpiAwareness</span><span class="sxs-lookup"><span data-stu-id="fc7a9-169">DpiAwareness</span></span>

<span data-ttu-id="fc7a9-170">從.NET Framework 4.7 下開頭為 Windows 10 建立者 Edition 和.NET Framework 目標版本的 Windows 版本所執行的 Windows Forms 應用程式可以設定為充分利用.NET Framework 中引進的高 DPI 改良功能4.7。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-170">Windows Forms apps that run under Windows versions starting with Windows 10 Creators Edition and target versions of the .NET Framework starting with the .NET Framework 4.7 can be configured to take advantage of high DPI improvements introduced in the .NET Framework 4.7.</span></span> <span data-ttu-id="fc7a9-171">這些活動包括：</span><span class="sxs-lookup"><span data-stu-id="fc7a9-171">These include:</span></span>

- <span data-ttu-id="fc7a9-172">支援動態 DPI 案例，已啟動的 Windows Form 應用程式之後變更 DPI 或小數位數因素的使用者。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-172">Support for dynamic DPI scenarios in which the user changes the DPI or scale factor after a Windows Forms application has been launched.</span></span>

- <span data-ttu-id="fc7a9-173">改良的縮放比例和 Windows Form 的數字的版面配置控制項，例如<xref:System.Windows.Forms.MonthCalendar>控制項和<xref:System.Windows.Forms.CheckedListBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-173">Improvements in the scaling and layout of a number of Windows Forms controls, such as the <xref:System.Windows.Forms.MonthCalendar> control and the <xref:System.Windows.Forms.CheckedListBox> control.</span></span> 

<span data-ttu-id="fc7a9-174">高 DPI 感知是選擇性功能。根據預設，值`DpiAwareness`是`false`。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-174">High DPI awareness is an opt-in feature; by default, the value of `DpiAwareness` is `false`.</span></span> <span data-ttu-id="fc7a9-175">您可以選擇為 Windows Form 支援 DPI 感知藉由設定此機碼值`PerMonitorV2`應用程式組態檔中。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-175">You can opt into Windows Forms' support for DPI awareness by setting the value of this key to `PerMonitorV2` in the application configuration file.</span></span> <span data-ttu-id="fc7a9-176">如果啟用 DPI 感知，則也會啟用所有的個別 DPI 功能。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-176">If DPI awareness is enabled, all individual DPI features are also enabled.</span></span> <span data-ttu-id="fc7a9-177">這些活動包括：</span><span class="sxs-lookup"><span data-stu-id="fc7a9-177">These include:</span></span>

- <span data-ttu-id="fc7a9-178">DPI 變更所控制的訊息`DisableDpiChangedMessageHandling`索引鍵。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-178">DPI changed messages, which are controlled by the `DisableDpiChangedMessageHandling` key.</span></span>

- <span data-ttu-id="fc7a9-179">動態 DPI 支援，由`EnableWindowsFormsHighDpiAutoResizing`索引鍵。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-179">Dynamic DPI support, which is controlled by the `EnableWindowsFormsHighDpiAutoResizing` key.</span></span>

- <span data-ttu-id="fc7a9-180">單次控制項縮放比例，這由`Form.DisableSinglePassControlScaling`個別<xref:System.Windows.Forms.Form>控制項，藉由`AnchorLayout.DisableSinglePassControlScaling`錨定的控制項，以及索引鍵`MonthCalendar.DisableSinglePassControlScaling`金鑰<xref:System.Windows.Forms.MonthCalendar>控制項</span><span class="sxs-lookup"><span data-stu-id="fc7a9-180">Single-pass control scaling, which is controlled by the `Form.DisableSinglePassControlScaling` for individual <xref:System.Windows.Forms.Form> controls, by the `AnchorLayout.DisableSinglePassControlScaling` key for anchored controls, and by the `MonthCalendar.DisableSinglePassControlScaling` key for the <xref:System.Windows.Forms.MonthCalendar> control</span></span> 

- <span data-ttu-id="fc7a9-181">高 DPI 縮放比例和配置的增強功能，由`CheckListBox.DisableHighDpiImprovements`金鑰<xref:System.Windows.Forms.CheckedListBox>藉由控制`DataGridView.DisableHighDpiImprovements`金鑰<xref:System.Windows.Forms.DataGridView>控制項，並依據`Toolstrip.DisableHighDpiImprovements`金鑰<xref:System.Windows.Forms.ToolStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-181">High DPI scaling and layout improvements, which is controlled by the `CheckListBox.DisableHighDpiImprovements` key for the <xref:System.Windows.Forms.CheckedListBox> control, by the `DataGridView.DisableHighDpiImprovements` key for the <xref:System.Windows.Forms.DataGridView> control, and by the `Toolstrip.DisableHighDpiImprovements` key for the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  

<span data-ttu-id="fc7a9-182">提供藉由設定中，選擇設定單一預設`DpiAwareness`至`PerMonitorV2`通常適合新的 Windows Form 應用程式。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-182">The single default opt-in setting provided by setting `DpiAwareness` to `PerMonitorV2` is generally adequate for new Windows Forms applications.</span></span> <span data-ttu-id="fc7a9-183">不過，您可以再退出個別的高 DPI 改進將對應的索引鍵加入至應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-183">However, You can then opt out of individual high DPI improvements by adding the corresponding key to the application configuration file.</span></span> <span data-ttu-id="fc7a9-184">比方說，若要利用所有除了動態 DPI 支援新 DPI featuers，您可以加入下列應用程式組態檔：</span><span class="sxs-lookup"><span data-stu-id="fc7a9-184">For example, to take advantage of all the new DPI featuers except for dynamic DPI support, you would add the following to your application configuration file:</span></span>

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <--! Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```
<span data-ttu-id="fc7a9-185">一般而言，您退出特定功能因為您已選擇要以程式設計方式處理。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-185">Typically, you opt out of a particular feature because you've chosen to handle it programmatically.</span></span>

<span data-ttu-id="fc7a9-186">如需如何利用 Windows Form 應用程式中的高 DPI 支援的詳細資訊，請參閱[Windows Form 中的高 DPI 支援](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-186">For more information on taking advantage of High DPI support in Windows Forms applications, see [High DPI Support in Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).</span></span>
 
### <a name="disabledpichangedmessagehandling"></a><span data-ttu-id="fc7a9-187">DisableDpiChangedMessageHandling</span><span class="sxs-lookup"><span data-stu-id="fc7a9-187">DisableDpiChangedMessageHandling</span></span>

<span data-ttu-id="fc7a9-188">從.NET Framework 4.7 開始，Windows Form 控制項引發的 DPI 縮放比例的變更相關的事件數目。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-188">Starting with the .NET Framework 4.7, Windows Forms controls raise a number of events related to changes in DPI scaling.</span></span> <span data-ttu-id="fc7a9-189">這些包括<xref:System.Windows.Forms.Control.DpiChangedAfterParent>， <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>，和<xref:System.Windows.Forms.Form.DpiChanged>事件。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-189">These include the <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, and <xref:System.Windows.Forms.Form.DpiChanged> events.</span></span> <span data-ttu-id="fc7a9-190">值`DisableDpiChangedMessageHandling`機碼決定是否在 Windows Form 應用程式中引發這些事件。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-190">The value of the `DisableDpiChangedMessageHandling` key determines whether these events are raised in a Windows Forms application.</span></span> 

### <a name="single-pass-scaling"></a><span data-ttu-id="fc7a9-191">單次縮放比例</span><span class="sxs-lookup"><span data-stu-id="fc7a9-191">Single-pass scaling</span></span>

<span data-ttu-id="fc7a9-192">單一或多重傳遞縮放比例會影響使用者介面的認知的回應和視覺外觀的使用者介面項目，因為它們縮放。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-192">Single or multi-pass scaling influences the perceived responsiveness of the user interface and the the visual appearance of user interface elements as they are scaled.</span></span> <span data-ttu-id="fc7a9-193">從.NET Framework 4.7 開始，Windows Form 會使用單一行程縮放比例。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-193">Starting with the .NET Framework 4.7, Windows Forms uses single pass scaling.</span></span> <span data-ttu-id="fc7a9-194">在舊版的.NET Framework 中，透過多個行程，這造成部分控制項，以調整多個必須執行縮放比例。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-194">In previous versions of the .NET Framework, scaling was performed through multiple passes, which caused some controls to be scaled more than was necessary.</span></span> <span data-ttu-id="fc7a9-195">單一行程調整應該才可停用舊的行為取決於您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fc7a9-195">Single-pass scaling should only be disabled if your app depends on the old behavior.</span></span>  

## <a name="see-also"></a><span data-ttu-id="fc7a9-196">請參閱</span><span class="sxs-lookup"><span data-stu-id="fc7a9-196">See also</span></span>
 
<span data-ttu-id="fc7a9-197">[Windows Form 的組態區段](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md) </span><span class="sxs-lookup"><span data-stu-id="fc7a9-197">[Windows Forms Configuration Section](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md) </span></span>  
[<span data-ttu-id="fc7a9-198">Windows Forms 中的高 DPI 支援</span><span class="sxs-lookup"><span data-stu-id="fc7a9-198">High DPI Support in Windows Forms</span></span>](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
