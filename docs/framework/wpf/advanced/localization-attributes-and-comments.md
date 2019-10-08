---
title: 當地語系化屬性和註解
ms.date: 03/30/2017
helpviewer_keywords:
- localization [WPF], attributes
- localization [WPF], comments
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
ms.openlocfilehash: 4f9c2700d8163988b7ea1e75bec1427778cf571c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004901"
---
# <a name="localization-attributes-and-comments"></a><span data-ttu-id="ea070-102">當地語系化屬性和註解</span><span class="sxs-lookup"><span data-stu-id="ea070-102">Localization Attributes and Comments</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="ea070-103">當地語系化批註是 XAML 原始程式碼內的屬性，由開發人員提供，以提供當地語系化的規則和提示。</span><span class="sxs-lookup"><span data-stu-id="ea070-103">localization comments are properties, inside XAML source code, supplied by developers to provide rules and hints for localization.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="ea070-104">當地語系化註解包含兩組資訊︰可當地語系化屬性和自由格式當地語系化註解。</span><span class="sxs-lookup"><span data-stu-id="ea070-104">localization comments contain two sets of information: localizability attributes and free-form localization comments.</span></span> <span data-ttu-id="ea070-105">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 當地語系化 API 使用可當地語系化屬性來指出要當地語系化的資源。</span><span class="sxs-lookup"><span data-stu-id="ea070-105">Localizability attributes are used by the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Localization API to indicate which resources are to be localized.</span></span> <span data-ttu-id="ea070-106">自由格式註解是應用程式作者想要包含的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="ea070-106">Free-form comments are any information that the application author wants to include.</span></span>  

<a name="Localizer_Comments_"></a>   
## <a name="localization-comments"></a><span data-ttu-id="ea070-107">當地語系化註解</span><span class="sxs-lookup"><span data-stu-id="ea070-107">Localization Comments</span></span>  
 <span data-ttu-id="ea070-108">如果標記應用程式作者有 XAML 中特定元素的需求，例如文字長度、字型系列或字型大小的條件約束，則可以將此資訊傳達給當地語系化人員，並在 XAML 程式碼中加上批註。</span><span class="sxs-lookup"><span data-stu-id="ea070-108">If markup application authors have requirements for specific elements in XAML, such as constraints on text length, font family, or font size, they can convey this information to localizers with comments in the XAML code.</span></span> <span data-ttu-id="ea070-109">將註解新增至原始程式碼的程序如下︰</span><span class="sxs-lookup"><span data-stu-id="ea070-109">The process for adding comments to source code is as follows:</span></span>  
  
1. <span data-ttu-id="ea070-110">應用程式開發人員會將當地語系化批註新增至 XAML 原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="ea070-110">Application developer adds localization comments to XAML source code.</span></span>  
  
2. <span data-ttu-id="ea070-111">在建置過程，您可以於 .proj 檔案中指定是否要保留組件中的自由格式當地語系化註解、去除註解的一部分，或去除所有註解。</span><span class="sxs-lookup"><span data-stu-id="ea070-111">During the build process, you can specify in the .proj file whether to leave the free-form localization comments in the assembly, strip out part of the comments, or strip out all the comments.</span></span> <span data-ttu-id="ea070-112">去除的註解會放在不同的檔案中。</span><span class="sxs-lookup"><span data-stu-id="ea070-112">The stripped-out comments are placed in a separate file.</span></span> <span data-ttu-id="ea070-113">您可以使用 `LocalizationDirectivesToLocFile` 標記來指定選項，例如︰</span><span class="sxs-lookup"><span data-stu-id="ea070-113">You specify your option using a `LocalizationDirectivesToLocFile` tag, eg:</span></span>  
  
     <span data-ttu-id="ea070-114">`<LocalizationDirectivesToLocFile>` <值> `</LocalizationDirectivesToLocFile>`</span><span class="sxs-lookup"><span data-stu-id="ea070-114">`<LocalizationDirectivesToLocFile>` *value* `</LocalizationDirectivesToLocFile>`</span></span>  
  
3. <span data-ttu-id="ea070-115">可以指派的值如下︰</span><span class="sxs-lookup"><span data-stu-id="ea070-115">The values that can be assigned are:</span></span>  
  
    - <span data-ttu-id="ea070-116">**None** - 註解和屬性會保留在組件內，而且不會產生個別檔案。</span><span class="sxs-lookup"><span data-stu-id="ea070-116">**None** - Both comments and attributes stay inside the assembly and no separate file is generated.</span></span>  
  
    - <span data-ttu-id="ea070-117">**CommentsOnly** - 只去除組件中的註解，並將它們放在個別 LocFile 中。</span><span class="sxs-lookup"><span data-stu-id="ea070-117">**CommentsOnly** - Strips only the comments from the assembly and places them in the separate LocFile.</span></span>  
  
    - <span data-ttu-id="ea070-118">**All** - 去除組件中的註解和屬性，並將它們放在個別 LocFile 中。</span><span class="sxs-lookup"><span data-stu-id="ea070-118">**All** - Strips both the comments and the attributes from the assembly and places them both in a separate LocFile.</span></span>  
  
4. <span data-ttu-id="ea070-119">從 BAML 解壓縮可當地語系化的資源時，BAML 當地語系化 API 會遵守可當地語系化的屬性。</span><span class="sxs-lookup"><span data-stu-id="ea070-119">When localizable resources are extracted from BAML, the localizability attributes are respected by the BAML Localization API.</span></span>  
  
5. <span data-ttu-id="ea070-120">稍後，只包含自由格式註解的當地語系化註解檔案會併入當地語系化程序。</span><span class="sxs-lookup"><span data-stu-id="ea070-120">Localization comment files, containing only free-form comments, are incorporated into the localization process at a later time.</span></span>  
  
 <span data-ttu-id="ea070-121">下列範例顯示如何將當地語系化批註加入至 XAML 檔案。</span><span class="sxs-lookup"><span data-stu-id="ea070-121">The following example shows how to add localization comments to a XAML file.</span></span>  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 <span data-ttu-id="ea070-122">在先前的範例中，Localization.Attributes 區段包含當地語系化屬性，而 Localization.Comments 區段包含自由格式註解。</span><span class="sxs-lookup"><span data-stu-id="ea070-122">In the previous sample the Localization.Attributes section contains the localization attributes and the Localization.Comments section the free-form comments.</span></span> <span data-ttu-id="ea070-123">下列各表顯示屬性和註解和其對當地語系化人員的意義。</span><span class="sxs-lookup"><span data-stu-id="ea070-123">The following tables show the attributes and comments and their meaning to the localizer.</span></span>  
  
|<span data-ttu-id="ea070-124">當地語系化屬性</span><span class="sxs-lookup"><span data-stu-id="ea070-124">Localization attributes</span></span>|<span data-ttu-id="ea070-125">意義</span><span class="sxs-lookup"><span data-stu-id="ea070-125">Meaning</span></span>|  
|-----------------------------|-------------|  
|<span data-ttu-id="ea070-126">$Content (無法修改的可讀取文字)</span><span class="sxs-lookup"><span data-stu-id="ea070-126">$Content (Unmodifiable Readable Text)</span></span>|<span data-ttu-id="ea070-127">無法修改 TextBlock 項目的內容。</span><span class="sxs-lookup"><span data-stu-id="ea070-127">Contents of the TextBlock element cannot be modified.</span></span> <span data-ttu-id="ea070-128">當地語系化人員無法變更 "Microsoft" 這個字。</span><span class="sxs-lookup"><span data-stu-id="ea070-128">Localizers cannot change the word "Microsoft".</span></span> <span data-ttu-id="ea070-129">當地語系化人員可以看到內容 (可讀取)。</span><span class="sxs-lookup"><span data-stu-id="ea070-129">The content is visible (Readable) to the localizer.</span></span> <span data-ttu-id="ea070-130">內容的分類為文字。</span><span class="sxs-lookup"><span data-stu-id="ea070-130">The category of the content is text.</span></span>|  
|<span data-ttu-id="ea070-131">FontFamily (無法修改的可讀取)</span><span class="sxs-lookup"><span data-stu-id="ea070-131">FontFamily (Unmodifiable Readable)</span></span>|<span data-ttu-id="ea070-132">無法變更 TextBlock 項目的字型家族屬性，但當地語系化人員可以看到它。</span><span class="sxs-lookup"><span data-stu-id="ea070-132">The font family property of the TextBlock element cannot be changed but it is visible to the localizer.</span></span>|  
  
|<span data-ttu-id="ea070-133">當地語系化自由格式註解</span><span class="sxs-lookup"><span data-stu-id="ea070-133">Localization free-form comments</span></span>|<span data-ttu-id="ea070-134">意義</span><span class="sxs-lookup"><span data-stu-id="ea070-134">Meaning</span></span>|  
|--------------------------------------|-------------|  
|<span data-ttu-id="ea070-135">$Content (商標)</span><span class="sxs-lookup"><span data-stu-id="ea070-135">$Content (Trademark)</span></span>|<span data-ttu-id="ea070-136">應用程式作者會告知當地語系化人員：TextBlock 項目中的內容是商標。</span><span class="sxs-lookup"><span data-stu-id="ea070-136">The application author tells the localizer that the content in the TextBlock element is a trademark.</span></span>|  
|<span data-ttu-id="ea070-137">FontSize (商標字型大小)</span><span class="sxs-lookup"><span data-stu-id="ea070-137">FontSize (Trademark font size)</span></span>|<span data-ttu-id="ea070-138">應用程式作者指出字型大小屬性應該遵循標準商標大小。</span><span class="sxs-lookup"><span data-stu-id="ea070-138">The application author indicates that the font size property should follow the standard trademark size.</span></span>|  
  
### <a name="localizability-attributes"></a><span data-ttu-id="ea070-139">可當地語系化屬性</span><span class="sxs-lookup"><span data-stu-id="ea070-139">Localizability Attributes</span></span>  
 <span data-ttu-id="ea070-140">Localization.Attributes 中的資訊包含配對的清單︰目標值名稱和相關聯的可當地語系化值。</span><span class="sxs-lookup"><span data-stu-id="ea070-140">The information in Localization.Attributes contains a list of pairs: the targeted value name and the associated localizability values.</span></span> <span data-ttu-id="ea070-141">目標名稱可以是屬性名稱或特殊 $Content 名稱。</span><span class="sxs-lookup"><span data-stu-id="ea070-141">The target name can be a property name or the special $Content name.</span></span> <span data-ttu-id="ea070-142">如果這是屬性名稱，則目標值是屬性的值。</span><span class="sxs-lookup"><span data-stu-id="ea070-142">If it is a property name, the targeted value is the value of the property.</span></span> <span data-ttu-id="ea070-143">如果是 $Content，則目標值是項目的內容。</span><span class="sxs-lookup"><span data-stu-id="ea070-143">If it is $Content, the target value is the content of the element.</span></span>  
  
 <span data-ttu-id="ea070-144">屬性有三種類型：</span><span class="sxs-lookup"><span data-stu-id="ea070-144">There are three types of attributes:</span></span>  
  
- <span data-ttu-id="ea070-145">**分類**.</span><span class="sxs-lookup"><span data-stu-id="ea070-145">**Category**.</span></span> <span data-ttu-id="ea070-146">這指定是否應該可以從當地語系化人員工具修改值。</span><span class="sxs-lookup"><span data-stu-id="ea070-146">This specifies whether a value should be modifiable from a localizer tool.</span></span> <span data-ttu-id="ea070-147">請參閱 <xref:System.Windows.LocalizabilityAttribute.Category%2A>。</span><span class="sxs-lookup"><span data-stu-id="ea070-147">See <xref:System.Windows.LocalizabilityAttribute.Category%2A>.</span></span>  
  
- <span data-ttu-id="ea070-148">**可讀性**.</span><span class="sxs-lookup"><span data-stu-id="ea070-148">**Readability**.</span></span> <span data-ttu-id="ea070-149">這指定當地語系化人員工具是否應該讀取 (和顯示) 值。</span><span class="sxs-lookup"><span data-stu-id="ea070-149">This specifies whether a localizer tool should read (and display) a value.</span></span> <span data-ttu-id="ea070-150">請參閱 <xref:System.Windows.LocalizabilityAttribute.Readability%2A>。</span><span class="sxs-lookup"><span data-stu-id="ea070-150">See <xref:System.Windows.LocalizabilityAttribute.Readability%2A>.</span></span>  
  
- <span data-ttu-id="ea070-151">**可修改性**.</span><span class="sxs-lookup"><span data-stu-id="ea070-151">**Modifiability**.</span></span> <span data-ttu-id="ea070-152">這指定當地語系化人員工具是否允許修改值。</span><span class="sxs-lookup"><span data-stu-id="ea070-152">This specifies whether a localizer tool allows a value to be modified.</span></span> <span data-ttu-id="ea070-153">請參閱 <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>。</span><span class="sxs-lookup"><span data-stu-id="ea070-153">See <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>.</span></span>  
  
 <span data-ttu-id="ea070-154">這些屬性可以依任何順序指定，並以空格分隔。</span><span class="sxs-lookup"><span data-stu-id="ea070-154">These attributes can be specified in any order delimited by a space.</span></span> <span data-ttu-id="ea070-155">如果指定重複屬性，則最後一個屬性會覆寫先前的屬性。</span><span class="sxs-lookup"><span data-stu-id="ea070-155">In case duplicate attributes are specified, the last attribute will override former ones.</span></span> <span data-ttu-id="ea070-156">例如，Localization.Attributes = "Unmodifiable Modifiable" 會將「可修改性」設定為「可修改」，因為它是最後一個值。</span><span class="sxs-lookup"><span data-stu-id="ea070-156">For example, Localization.Attributes = "Unmodifiable Modifiable" sets Modifiability to Modifiable because it is the last value.</span></span>  
  
 <span data-ttu-id="ea070-157">可修改性和可讀性一看就懂。</span><span class="sxs-lookup"><span data-stu-id="ea070-157">Modifiability and Readability are self-explanatory.</span></span> <span data-ttu-id="ea070-158">分類屬性提供預先定義的分類，以在翻譯文字時協助當地語系化人員。</span><span class="sxs-lookup"><span data-stu-id="ea070-158">The Category attribute provides predefined categories that help the localizer when translating text.</span></span> <span data-ttu-id="ea070-159">文字、標籤和標題這類分類會將如何翻譯文字的資訊提供給當地語系化人員。</span><span class="sxs-lookup"><span data-stu-id="ea070-159">Categories, such as, Text, Label, and Title give the localizer information about how to translate the text.</span></span> <span data-ttu-id="ea070-160">另外還有特殊類別：[無]、[繼承]、[忽略] 和 [NeverLocalize]。</span><span class="sxs-lookup"><span data-stu-id="ea070-160">There are also special categories: None, Inherit, Ignore, and NeverLocalize.</span></span>  
  
 <span data-ttu-id="ea070-161">下表顯示特殊分類的意義。</span><span class="sxs-lookup"><span data-stu-id="ea070-161">The following table shows the meaning of the special categories.</span></span>  
  
|<span data-ttu-id="ea070-162">Category</span><span class="sxs-lookup"><span data-stu-id="ea070-162">Category</span></span>|<span data-ttu-id="ea070-163">意義</span><span class="sxs-lookup"><span data-stu-id="ea070-163">Meaning</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="ea070-164">None</span><span class="sxs-lookup"><span data-stu-id="ea070-164">None</span></span>|<span data-ttu-id="ea070-165">目標值沒有已定義的分類。</span><span class="sxs-lookup"><span data-stu-id="ea070-165">Targeted value has no defined category.</span></span>|  
|<span data-ttu-id="ea070-166">繼承</span><span class="sxs-lookup"><span data-stu-id="ea070-166">Inherit</span></span>|<span data-ttu-id="ea070-167">目標值會從其父代繼承其分類。</span><span class="sxs-lookup"><span data-stu-id="ea070-167">Targeted value inherits its category from its parent.</span></span>|  
|<span data-ttu-id="ea070-168">Ignore</span><span class="sxs-lookup"><span data-stu-id="ea070-168">Ignore</span></span>|<span data-ttu-id="ea070-169">會略過當地語系化程序中的目標值。</span><span class="sxs-lookup"><span data-stu-id="ea070-169">Targeted value is ignored in the localization process.</span></span> <span data-ttu-id="ea070-170">略過只會影響目前值。</span><span class="sxs-lookup"><span data-stu-id="ea070-170">Ignore affects only the current value.</span></span> <span data-ttu-id="ea070-171">它不會影響子節點。</span><span class="sxs-lookup"><span data-stu-id="ea070-171">It will not affect child nodes.</span></span>|  
|<span data-ttu-id="ea070-172">NeverLocalize</span><span class="sxs-lookup"><span data-stu-id="ea070-172">NeverLocalize</span></span>|<span data-ttu-id="ea070-173">無法當地語系化目前值。</span><span class="sxs-lookup"><span data-stu-id="ea070-173">Current value cannot be localized.</span></span> <span data-ttu-id="ea070-174">項目的子系會繼承此分類。</span><span class="sxs-lookup"><span data-stu-id="ea070-174">This category is inherited by the children of an element.</span></span>|  
  
<a name="Localization_Comments"></a>   
## <a name="localization-comments"></a><span data-ttu-id="ea070-175">當地語系化註解</span><span class="sxs-lookup"><span data-stu-id="ea070-175">Localization Comments</span></span>  
 <span data-ttu-id="ea070-176">Localization.Comments 包含有關目標值的自由格式字串。</span><span class="sxs-lookup"><span data-stu-id="ea070-176">Localization.Comments contains free-form strings concerning the targeted value.</span></span> <span data-ttu-id="ea070-177">應用程式開發人員可以新增資訊，提供當地語系化人員如何翻譯應用程式文字的提示。</span><span class="sxs-lookup"><span data-stu-id="ea070-177">Application developers can add information to give localizers hints about how the applications text should be translated.</span></span> <span data-ttu-id="ea070-178">註解的格式可以是用 "()" 括住的任何字串。</span><span class="sxs-lookup"><span data-stu-id="ea070-178">The format of the comments can be any string surrounded by "()".</span></span> <span data-ttu-id="ea070-179">使用 '\\' 來逸出字元。</span><span class="sxs-lookup"><span data-stu-id="ea070-179">Use '\\' to escape characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea070-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea070-180">See also</span></span>

- [<span data-ttu-id="ea070-181">WPF 的全球化</span><span class="sxs-lookup"><span data-stu-id="ea070-181">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="ea070-182">使用自動版面配置建立按鈕</span><span class="sxs-lookup"><span data-stu-id="ea070-182">Use Automatic Layout to Create a Button</span></span>](how-to-use-automatic-layout-to-create-a-button.md)
- [<span data-ttu-id="ea070-183">針對自動版面配置使用方格</span><span class="sxs-lookup"><span data-stu-id="ea070-183">Use a Grid for Automatic Layout</span></span>](how-to-use-a-grid-for-automatic-layout.md)
- [<span data-ttu-id="ea070-184">將應用程式當地語系化</span><span class="sxs-lookup"><span data-stu-id="ea070-184">Localize an Application</span></span>](how-to-localize-an-application.md)
