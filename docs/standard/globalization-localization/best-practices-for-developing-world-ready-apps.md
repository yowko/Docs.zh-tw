---
title: 開發世界性的應用程式的最佳作法
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- global applications, best practices
- world-ready applications, best practices
- globalization [.NET Framework], best practices
- international applications [.NET Framework], best practices
ms.assetid: f08169c7-aad8-4ec3-9a21-9ebd3b89986c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d96e223b85178c7f2784a523e5609057d1432488
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310534"
---
# <a name="best-practices-for-developing-world-ready-applications"></a><span data-ttu-id="c2c2d-102">開發世界性應用程式的最佳做法</span><span class="sxs-lookup"><span data-stu-id="c2c2d-102">Best practices for developing world-ready applications</span></span>

<span data-ttu-id="c2c2d-103">本章節將說明開發世界性的應用程式的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-103">This section describes the best practices to follow when developing world-ready applications.</span></span>

## <a name="globalization-best-practices"></a><span data-ttu-id="c2c2d-104">全球化最佳做法</span><span class="sxs-lookup"><span data-stu-id="c2c2d-104">Globalization best practices</span></span>

1. <span data-ttu-id="c2c2d-105">請在內部製作您的應用程式 Unicode。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-105">Make your application Unicode internally.</span></span>

2. <span data-ttu-id="c2c2d-106">使用 <xref:System.Globalization> 命名空間提供的文化特性感知類別來管理和格式化資料。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-106">Use the culture-aware classes provided by the <xref:System.Globalization> namespace to manipulate and format data.</span></span>

    - <span data-ttu-id="c2c2d-107">如需排序，請使用 <xref:System.Globalization.SortKey> 類別和 <xref:System.Globalization.CompareInfo> 類別。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-107">For sorting, use the <xref:System.Globalization.SortKey> class and the <xref:System.Globalization.CompareInfo> class.</span></span>

    - <span data-ttu-id="c2c2d-108">如需字串比較，請使用 <xref:System.Globalization.CompareInfo> 類別。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-108">For string comparisons, use the <xref:System.Globalization.CompareInfo> class.</span></span>

    - <span data-ttu-id="c2c2d-109">如需日期和時間格式化，請使用 <xref:System.Globalization.DateTimeFormatInfo> 類別。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-109">For date and time formatting, use the <xref:System.Globalization.DateTimeFormatInfo> class.</span></span>

    - <span data-ttu-id="c2c2d-110">如需數字格式化，請使用 <xref:System.Globalization.NumberFormatInfo> 類別。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-110">For numeric formatting, use the <xref:System.Globalization.NumberFormatInfo> class.</span></span>

    - <span data-ttu-id="c2c2d-111">對於西曆和非西曆，請使用 <xref:System.Globalization.Calendar> 類別或其中一個特定曆法實作。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-111">For Gregorian and non-Gregorian calendars, use the <xref:System.Globalization.Calendar> class or one of the specific calendar implementations.</span></span>

3. <span data-ttu-id="c2c2d-112">在適當情況下使用 <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> 類別提供的文化特性屬性設定。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-112">Use the culture property settings provided by the <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> class in the appropriate situations.</span></span> <span data-ttu-id="c2c2d-113">使用 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 屬性來格式化工作，例如日期和時間或數字格式化。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-113">Use the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> property for formatting tasks, such as date and time or numeric formatting.</span></span> <span data-ttu-id="c2c2d-114">使用 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> 屬性來擷取資源。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-114">Use the <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> property to retrieve resources.</span></span> <span data-ttu-id="c2c2d-115">請注意，您可以根據個別執行緒來設定 `CurrentCulture` 和 `CurrentUICulture` 屬性。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-115">Note that the `CurrentCulture` and `CurrentUICulture` properties can be set per thread.</span></span>

4. <span data-ttu-id="c2c2d-116">啟用您的應用程式使用 <xref:System.Text> 命名空間中的編碼類別來回讀取和寫入各種編碼方式的資料。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-116">Enable your application to read and write data to and from a variety of encodings by using the encoding classes in the <xref:System.Text> namespace.</span></span> <span data-ttu-id="c2c2d-117">請勿假設 ASCII 資料。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-117">Do not assume ASCII data.</span></span> <span data-ttu-id="c2c2d-118">請假設在使用中輸入文字的地方提供國際字元。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-118">Assume that international characters will be supplied anywhere a user can enter text.</span></span> <span data-ttu-id="c2c2d-119">例如，應用程式應該會接受在伺服器名稱、目錄、檔名和 URL 中使用國際字元。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-119">For example, the application should accept international characters in server names, directories, file names, user names, and URLs.</span></span>

5. <span data-ttu-id="c2c2d-120">在使用 <xref:System.Text.UTF8Encoding> 類別時，基於安全理由，請使用這個類別所提供的錯誤偵測功能。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-120">When using the <xref:System.Text.UTF8Encoding> class, for security reasons, use the error detection feature offered by this class.</span></span> <span data-ttu-id="c2c2d-121">若要開啟錯誤偵測功能，請使用採用 `throwOnInvalidBytes` 參數的建構函式，並將此參數的值設定為 `true`，以建立此類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-121">To turn on the error detection feature, create an instance of the class using the constructor that takes a `throwOnInvalidBytes` parameter and set the value of this parameter to `true`.</span></span>

6. <span data-ttu-id="c2c2d-122">如果可能的話，請將字串當做完整的字串處理，而不是連續的個別字串。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-122">Whenever possible, handle strings as entire strings instead of as a series of individual characters.</span></span> <span data-ttu-id="c2c2d-123">在排序或搜尋子字串時，這點特別重要。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-123">This is especially important when sorting or searching for substrings.</span></span> <span data-ttu-id="c2c2d-124">它將可避免發生剖析組合字元的相關問題。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-124">This will prevent problems associated with parsing combined characters.</span></span> <span data-ttu-id="c2c2d-125">您也可利用 <xref:System.Globalization.StringInfo?displayProperty=nameWithType> 類別，便無須使用單一字元，而是以單位來使用文字。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-125">You can also work with units of text rather than single characters by using the <xref:System.Globalization.StringInfo?displayProperty=nameWithType> class.</span></span>

7. <span data-ttu-id="c2c2d-126">使用 <xref:System.Drawing> 命名空間提供類別來顯示文字。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-126">Display text using the classes provided by the <xref:System.Drawing> namespace.</span></span>

8. <span data-ttu-id="c2c2d-127">為了作業系統的一致性，請勿使用使用者設定來覆寫 <xref:System.Globalization.CultureInfo>。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-127">For consistency across operating systems, do not allow user settings to override <xref:System.Globalization.CultureInfo>.</span></span> <span data-ttu-id="c2c2d-128">請使用採用 `CultureInfo` 參數的 `useUserOverride` 建構函式，並將此參數設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-128">Use the `CultureInfo` constructor that accepts a `useUserOverride` parameter and set it to `false`.</span></span>

9. <span data-ttu-id="c2c2d-129">使用國際資料，在國際作業系統版本上測試您的應用程式功能。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-129">Test your application functionality on international operating system versions, using international data.</span></span>

10. <span data-ttu-id="c2c2d-130">如果安全性決策是根據字串比較或大小寫變更作業的結果而定，則請使用不區分文化特性 (Culture) 的字串作業。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-130">If a security decision is based on the result of a string comparison or case change operation, use a culture-insensitive string operation.</span></span> <span data-ttu-id="c2c2d-131">這種作法可以確保結果不會受 `CultureInfo.CurrentCulture` 的值所影響。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-131">This practice ensures that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="c2c2d-132">如需示範區分文化特性 (Culture) 的字串比較如何產生不一致結果的範例，請參閱[使用字串的最佳做法](../../../docs/standard/base-types/best-practices-strings.md)中的[「使用目前文化特性 (Culture) 的字串比較」](../../../docs/standard/base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture)一節。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-132">See the ["String Comparisons that Use the Current Culture"](../../../docs/standard/base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) section of [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) for an example that demonstrates how culture-sensitive string comparisons can produce inconsistent results.</span></span>

## <a name="localization-best-practices"></a><span data-ttu-id="c2c2d-133">當地語系化最佳做法</span><span class="sxs-lookup"><span data-stu-id="c2c2d-133">Localization best practices</span></span>

1. <span data-ttu-id="c2c2d-134">將所有可當地語系化資源移到個別僅含資源的 DLL。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-134">Move all localizable resources to separate resource-only DLLs.</span></span> <span data-ttu-id="c2c2d-135">可當地語系化的資源包括使用者介面項目，例如字串、錯誤訊息、對話方塊、功能表和內嵌物件資源。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-135">Localizable resources include user interface elements, such as strings, error messages, dialog boxes, menus, and embedded object resources.</span></span>

2. <span data-ttu-id="c2c2d-136">請勿將字串或使用者介面資源寫在程式中。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-136">Do not hardcode strings or user interface resources.</span></span>

3. <span data-ttu-id="c2c2d-137">請勿將不可當地語系化的資源放入僅含資源的 DLL。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-137">Do not put nonlocalizable resources into the resource-only DLLs.</span></span> <span data-ttu-id="c2c2d-138">它將造成轉譯器的混淆。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-138">This causes confusion for translators.</span></span>

4. <span data-ttu-id="c2c2d-139">請勿使用在執行階段建置和來自連結字詞的複合字串。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-139">Do not use composite strings that are built at run time from concatenated phrases.</span></span> <span data-ttu-id="c2c2d-140">複合字串很難進行當地語系化，因為它們通常會使用不適用於所有語言的英文文法順序。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-140">Composite strings are difficult to localize because they often assume an English grammatical order that does not apply to all languages.</span></span>

5. <span data-ttu-id="c2c2d-141">避免模糊的建構，例如 "Empty Folder"，其中的字串將依據字串元件擔任的文法角色，而進行不同的轉譯。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-141">Avoid ambiguous constructs such as "Empty Folder" where the strings can be translated differently depending on the grammatical roles of the string components.</span></span> <span data-ttu-id="c2c2d-142">例如，"empty" 可以是動詞或形容詞，在某些語言中會有不同的轉譯結果，例如義大利文或法文。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-142">For example, "empty" can be either a verb or an adjective, which can lead to different translations in languages such as Italian or French.</span></span>

6. <span data-ttu-id="c2c2d-143">避免在您的應用程式中使用含有文字的影像和圖示。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-143">Avoid using images and icons that contain text in your application.</span></span> <span data-ttu-id="c2c2d-144">它們進行當地語系化的成本過高。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-144">They are expensive to localize.</span></span>

7. <span data-ttu-id="c2c2d-145">請保留充分的空間，以便在應用程式介面中擴展字串長度。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-145">Allow plenty of room for the length of strings to expand in the user interface.</span></span> <span data-ttu-id="c2c2d-146">在某些語言中，字詞所需要的空間可能比在其他語言多百分之 50-75。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-146">In some languages, phrases can require 50-75 percent more space than they need in other languages.</span></span>

8. <span data-ttu-id="c2c2d-147">使用 <xref:System.Resources.ResourceManager?displayProperty=nameWithType> 類別來根據文化特性擷取資源。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-147">Use the <xref:System.Resources.ResourceManager?displayProperty=nameWithType> class to retrieve resources based on culture.</span></span>

9. <span data-ttu-id="c2c2d-148">使用 [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) 建立 [Windows Forms] 對話方塊，如此就能使用 [Windows Forms 資源編輯器 (Winres.exe)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md) 將對話方塊當地語系化。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-148">Use [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) to create Windows Forms dialog boxes so they can be localized using the [Windows Forms Resource Editor (Winres.exe)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span></span> <span data-ttu-id="c2c2d-149">請不要以手動方式編碼 Windows Form 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-149">Do not code Windows Forms dialog boxes by hand.</span></span>

10. <span data-ttu-id="c2c2d-150">進行專業當地語系化 (轉譯)。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-150">Arrange for professional localization (translation).</span></span>

11. <span data-ttu-id="c2c2d-151">如需建立和當地語系化資源的完整描述，請參閱[應用程式中的資源](../../../docs/framework/resources/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-151">For a complete description of creating and localizing resources, see [Resources in Applications](../../../docs/framework/resources/index.md).</span></span>

## <a name="globalization-best-practices-for-aspnet-applications"></a><span data-ttu-id="c2c2d-152">ASP.NET 應用程式的全球化最佳做法</span><span class="sxs-lookup"><span data-stu-id="c2c2d-152">Globalization best practices for ASP.NET applications</span></span>

1. <span data-ttu-id="c2c2d-153">在應用程式中明確設定 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> 和 <xref:System.Globalization.CultureInfo.CurrentCulture%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-153">Explicitly set the <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> and <xref:System.Globalization.CultureInfo.CurrentCulture%2A> properties in your application.</span></span> <span data-ttu-id="c2c2d-154">請勿過於依賴預設值。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-154">Do not rely on defaults.</span></span>

2. <span data-ttu-id="c2c2d-155">請注意，ASP.NET 應用程式是 Managed 應用程式，因此可使用和其他 Managed 應用程式相同的類別，根據文化特性來擷取、顯示和管理資訊。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-155">Note that ASP.NET applications are managed applications and therefore can use the same classes as other managed applications for retrieving, displaying, and manipulating information based on culture.</span></span>

3. <span data-ttu-id="c2c2d-156">請注意，您可以指定下列三種 ASP.NET 中的編法方式類型：</span><span class="sxs-lookup"><span data-stu-id="c2c2d-156">Be aware that you can specify the following three types of encodings in ASP.NET:</span></span>

    - <span data-ttu-id="c2c2d-157">requestEncoding 指定從用戶端瀏覽器接收的編法方式。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-157">requestEncoding specifies the encoding received from the client's browser.</span></span>

    - <span data-ttu-id="c2c2d-158">responseEncoding 指定要傳送到用戶端瀏覽器的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-158">responseEncoding specifies the encoding to send to the client browser.</span></span> <span data-ttu-id="c2c2d-159">在多數情況下，此編碼方式應該與 requestEncoding 指定的編碼方式相同。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-159">In most situations, this encoding should be the same as that specified for requestEncoding.</span></span>

    - <span data-ttu-id="c2c2d-160">fileEncoding 指定 .aspx、.asmx 和 .asax 檔案剖析的預設編碼方式。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-160">fileEncoding specifies the default encoding for .aspx, .asmx, and .asax file parsing.</span></span>

4. <span data-ttu-id="c2c2d-161">指定 ASP.NET 應用程式中，下列三個位置的 requestEncoding、responseEncoding、fileEncoding、culture 和 uiCulture 屬性值：</span><span class="sxs-lookup"><span data-stu-id="c2c2d-161">Specify the values for the requestEncoding, responseEncoding, fileEncoding, culture, and uiCulture attributes in the following three places in an ASP.NET application:</span></span>

    - <span data-ttu-id="c2c2d-162">在 Web.config 檔案的全球化區段中。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-162">In the globalization section of a Web.config file.</span></span> <span data-ttu-id="c2c2d-163">這個程式位於 ASP.NET 應用程式外部。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-163">This file is external to the ASP.NET application.</span></span> <span data-ttu-id="c2c2d-164">如需詳細資訊，請參閱 [\<globalization> 元素](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hy4kkhe0(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-164">For more information, see [\<globalization> Element](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hy4kkhe0(v=vs.100)).</span></span>

    - <span data-ttu-id="c2c2d-165">在網頁指示詞中。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-165">In a page directive.</span></span> <span data-ttu-id="c2c2d-166">請注意，當應用程式位於網頁中，表示這個檔案已被讀取。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-166">Note that, when an application is in a page, the file has already been read.</span></span> <span data-ttu-id="c2c2d-167">因此，此時要指定 fileEncoding 和 requestEncoding 已經太遲了。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-167">Therefore, it is too late to specify fileEncoding and requestEncoding.</span></span> <span data-ttu-id="c2c2d-168">您只能在網頁指示詞中指定 uiCulture、Culture 和 responseEncoding。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-168">Only uiCulture, Culture, and responseEncoding can be specified in a page directive.</span></span>

    - <span data-ttu-id="c2c2d-169">應用程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-169">Programmatically in application code.</span></span> <span data-ttu-id="c2c2d-170">這個設定會根據個別要求而有所不同。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-170">This setting can vary per request.</span></span> <span data-ttu-id="c2c2d-171">和網頁指示詞一樣，使用應用程式碼時，表示要指定 fileEncoding 和 requestEncoding 已經太遲了。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-171">As with a page directive, by the time the application's code is reached it is too late to specify fileEncoding and requestEncoding.</span></span> <span data-ttu-id="c2c2d-172">您只能在應用程式碼中指定 uiCulture、Culture 和 responseEncoding。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-172">Only uiCulture, Culture, and responseEncoding can be specified in application code.</span></span>

5. <span data-ttu-id="c2c2d-173">請注意，uiCulture 值可設為瀏覽器所接受的語言。</span><span class="sxs-lookup"><span data-stu-id="c2c2d-173">Note that the uiCulture value can be set to the browser accept language.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2c2d-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2c2d-174">See also</span></span>

- [<span data-ttu-id="c2c2d-175">全球化和當地語系化</span><span class="sxs-lookup"><span data-stu-id="c2c2d-175">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
- [<span data-ttu-id="c2c2d-176">桌面應用程式中的資源</span><span class="sxs-lookup"><span data-stu-id="c2c2d-176">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
