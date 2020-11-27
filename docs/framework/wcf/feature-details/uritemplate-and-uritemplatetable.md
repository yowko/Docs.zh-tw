---
title: UriTemplate 與 UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: 212cc0a7f90ac2e74837118a905519148ddc089d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289668"
---
# <a name="uritemplate-and-uritemplatetable"></a><span data-ttu-id="bd5e7-102">UriTemplate 與 UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="bd5e7-102">UriTemplate and UriTemplateTable</span></span>

<span data-ttu-id="bd5e7-103">Web 開發人員需要能夠描述其服務所回應的 URI 形式與配置。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-103">Web developers require the ability to describe the shape and layout of the URIs that their services respond to.</span></span> <span data-ttu-id="bd5e7-104">Windows Communication Foundation (WCF) 加入了兩個新類別，讓開發人員能夠控制其 Uri。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-104">Windows Communication Foundation (WCF) added two new classes to give developers control over their URIs.</span></span> <span data-ttu-id="bd5e7-105"><xref:System.UriTemplate> 並 <xref:System.UriTemplateTable> 構成 WCF 中以 URI 為基礎的分派引擎基礎。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-105"><xref:System.UriTemplate> and <xref:System.UriTemplateTable> form the basis of the URI-based dispatch engine in WCF.</span></span> <span data-ttu-id="bd5e7-106">這些類別也可以單獨使用，讓開發人員可以利用範本和 URI 對應機制，而不需要執行 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-106">These classes can also be used on their own, allowing developers to take advantage of templates and the URI mapping mechanism without implementing a WCF service.</span></span>  
  
## <a name="templates"></a><span data-ttu-id="bd5e7-107">範本</span><span class="sxs-lookup"><span data-stu-id="bd5e7-107">Templates</span></span>  

 <span data-ttu-id="bd5e7-108">範本提供了一種用來描述相對 URI 集合的方式。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-108">A template is a way to describe a set of relative URIs.</span></span> <span data-ttu-id="bd5e7-109">下表中的 URI 範本集將說明如何定義負責擷取各種氣象資訊型別的系統。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-109">The set of URI templates in the following table shows how a system that retrieves various types of weather information might be defined.</span></span>  
  
|<span data-ttu-id="bd5e7-110">資料</span><span class="sxs-lookup"><span data-stu-id="bd5e7-110">Data</span></span>|<span data-ttu-id="bd5e7-111">範本</span><span class="sxs-lookup"><span data-stu-id="bd5e7-111">Template</span></span>|  
|----------|--------------|  
|<span data-ttu-id="bd5e7-112">國內趨勢預測</span><span class="sxs-lookup"><span data-stu-id="bd5e7-112">National Forecast</span></span>|<span data-ttu-id="bd5e7-113">weather/national</span><span class="sxs-lookup"><span data-stu-id="bd5e7-113">weather/national</span></span>|  
|<span data-ttu-id="bd5e7-114">各州趨勢預測</span><span class="sxs-lookup"><span data-stu-id="bd5e7-114">State Forecast</span></span>|<span data-ttu-id="bd5e7-115">weather/{state}</span><span class="sxs-lookup"><span data-stu-id="bd5e7-115">weather/{state}</span></span>|  
|<span data-ttu-id="bd5e7-116">城市趨勢預測</span><span class="sxs-lookup"><span data-stu-id="bd5e7-116">City Forecast</span></span>|<span data-ttu-id="bd5e7-117">weather/{state}/{city}</span><span class="sxs-lookup"><span data-stu-id="bd5e7-117">weather/{state}/{city}</span></span>|  
|<span data-ttu-id="bd5e7-118">活動趨勢預測</span><span class="sxs-lookup"><span data-stu-id="bd5e7-118">Activity Forecast</span></span>|<span data-ttu-id="bd5e7-119">weather/{state}/{city}/{activity}</span><span class="sxs-lookup"><span data-stu-id="bd5e7-119">weather/{state}/{city}/{activity}</span></span>|  
  
 <span data-ttu-id="bd5e7-120">這份表格說明結構上類似的 URI 集合。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-120">This table describes a set of structurally similar URIs.</span></span> <span data-ttu-id="bd5e7-121">每個項目都是 URI 範本。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-121">Each entry is a URI template.</span></span> <span data-ttu-id="bd5e7-122">大括號內的片段描述變數，</span><span class="sxs-lookup"><span data-stu-id="bd5e7-122">The segments in curly braces describe variables.</span></span> <span data-ttu-id="bd5e7-123">大括號外的片段則描述常值字串。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-123">The segments not in curly braces describe literal strings.</span></span> <span data-ttu-id="bd5e7-124">WCF 範本類別可讓開發人員接受傳入的 URI，例如 "/weather/wa/seattle/cycling"，並將它與描述它的範本 "/weather/{state}/{city}/{activity}" 進行比對。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-124">The WCF template classes allow a developer to take an incoming URI, for example, "/weather/wa/seattle/cycling", and match it to a template that describes it, "/weather/{state}/{city}/{activity}".</span></span>  
  
## <a name="uritemplate"></a><span data-ttu-id="bd5e7-125">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="bd5e7-125">UriTemplate</span></span>  

 <span data-ttu-id="bd5e7-126"><xref:System.UriTemplate> 是一個會封裝 URI 範本的類別。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-126"><xref:System.UriTemplate> is a class that encapsulates a URI template.</span></span> <span data-ttu-id="bd5e7-127">建構函式會包含用來定義範本的字串參數。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-127">The constructor takes a string parameter that defines the template.</span></span> <span data-ttu-id="bd5e7-128">此字串會將範本包含在下一節中說明的格式裡。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-128">This string contains the template in the format described in the next section.</span></span> <span data-ttu-id="bd5e7-129"><xref:System.UriTemplate> 類別所提供的方法可讓您將傳入的 URI 與範本進行比對、從範本產生 URI、擷取範本中使用的變數名稱集合，並判斷這兩個範本是否相等，然後傳回範本的字串。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-129">The <xref:System.UriTemplate> class provides methods that allow you match an incoming URI to a template, generate a URI from a template, retrieve a collection of variable names used in the template, determine whether two templates are equivalent, and return the template's string.</span></span>  
  
 <span data-ttu-id="bd5e7-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> 包含基底位址與候選 URI，並嘗試將 URI 與範本進行比對。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> takes a base address and a candidate URI and attempts to match the URI to the template.</span></span> <span data-ttu-id="bd5e7-131">如果比對成功，則會傳回 <xref:System.UriTemplateMatch> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-131">If the match is successful, a <xref:System.UriTemplateMatch> instance is returned.</span></span> <span data-ttu-id="bd5e7-132"><xref:System.UriTemplateMatch>物件包含一個起始 URI、一個候選 URI、一個查詢參數的名稱/值集合、一個相對路徑片段陣列、一個相符的變數名稱/值集合、用來執行比對的<xref:System.UriTemplate>執行個體、一個包含候選 URI (當範本包含萬用字元時所使用) 中任何不相符部分的字串，以及一個與範本相關聯的物件。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-132">The <xref:System.UriTemplateMatch> object contains a base URI, the candidate URI, a name/value collection of the query parameters, an array of the relative path segments, a name/value collection of variables that were matched, the <xref:System.UriTemplate> instance used to perform the match, a string that contains any unmatched portion of the candidate URI (used when the template has a wildcard), and an object that is associated with the template.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd5e7-133"><xref:System.UriTemplate> 類別在將範本與候選 URI 與進行比較時，會忽略配置和連接埠編號。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-133">The <xref:System.UriTemplate> class ignores the scheme and port number when matching a candidate URI to a template.</span></span>  
  
 <span data-ttu-id="bd5e7-134">有兩種方法可讓您從範本中產生 URI：<xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> 和 <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-134">There are two methods that allow you to generate a URI from a template, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> and <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span></span> <span data-ttu-id="bd5e7-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> 需要基底位址和參數的名稱/值集合。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> takes a base address and a name/value collection of parameters.</span></span> <span data-ttu-id="bd5e7-136">當範本經過繫結，就會以這些參數來取代變數。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-136">These parameters are substituted for variables when the template is bound.</span></span> <span data-ttu-id="bd5e7-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> 將會由左至右取代其接受的名稱/值組。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> takes the name/value pairs and substitutes them left to right.</span></span>  
  
 <span data-ttu-id="bd5e7-138"><xref:System.UriTemplate.ToString> 會傳回範本字串。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-138"><xref:System.UriTemplate.ToString> returns the template string.</span></span>  
  
 <span data-ttu-id="bd5e7-139"><xref:System.UriTemplate.PathSegmentVariableNames%2A> 屬性包含範本字串之路徑片段中所使用的變數名稱集合。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-139">The <xref:System.UriTemplate.PathSegmentVariableNames%2A> property contains a collection of the names of the variables used within path segments in the template string.</span></span>  
  
 <span data-ttu-id="bd5e7-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> 以 <xref:System.UriTemplate> 做為參數，並傳回布林值指出兩個範本是否相等。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> takes a <xref:System.UriTemplate> as a parameter and returns a Boolean value that specifies whether the two templates are equivalent.</span></span> <span data-ttu-id="bd5e7-141">如需詳細資訊，請參閱本主題稍後的「範本等價」一節。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-141">For more information, see the Template Equivalence section later in this topic.</span></span>  
  
 <span data-ttu-id="bd5e7-142"><xref:System.UriTemplate> 的設計即是可與符合 HTTP URI 文法的任何 URI 配置搭配使用。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-142"><xref:System.UriTemplate> is designed to work with any URI scheme that conforms to the HTTP URI grammar.</span></span> <span data-ttu-id="bd5e7-143">以下是支援的 URI 配置範例：</span><span class="sxs-lookup"><span data-stu-id="bd5e7-143">The following are examples of supported URI schemes.</span></span>  
  
- `http://`  
  
- `https://`  
  
- `net.tcp://`  
  
- `net.pipe://`  
  
- `sb://`  
  
 <span data-ttu-id="bd5e7-144">如 file:// 及 urn:// 的配置並不符合 HTTP URI 文法，若搭配 URI 範本使用，會造成無法預期的結果。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-144">Schemes like file:// and urn:// do not conform to the HTTP URI grammar and cause unpredictable results when used with URI templates.</span></span>  
  
### <a name="template-string-syntax"></a><span data-ttu-id="bd5e7-145">範本字串語法</span><span class="sxs-lookup"><span data-stu-id="bd5e7-145">Template String Syntax</span></span>  

 <span data-ttu-id="bd5e7-146">範本包含三大部分：路徑、選擇性查詢以及選擇性片段。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-146">A template has three parts: a path, an optional query, and an optional fragment.</span></span> <span data-ttu-id="bd5e7-147">例如，請參閱下列範本：</span><span class="sxs-lookup"><span data-stu-id="bd5e7-147">For an example, see the following template:</span></span>  
  
`"/weather/{state}/{city}?forecast={length)#frag1`  
  
 <span data-ttu-id="bd5e7-148">路徑包含 "/weather/{state}/{city}"，查詢包含 "?forecast={length}，而片段則包含 "#frag1"。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-148">The path consists of "/weather/{state}/{city}", the query consists of "?forecast={length}, and the fragment consists of "#frag1".</span></span>  
  
 <span data-ttu-id="bd5e7-149">路徑運算式中的前置與句尾斜線是選用的，</span><span class="sxs-lookup"><span data-stu-id="bd5e7-149">Leading and trailing slashes are optional in the path expression.</span></span> <span data-ttu-id="bd5e7-150">查詢與片段運算式可以全部省略掉。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-150">Both the query and fragment expressions can be omitted entirely.</span></span> <span data-ttu-id="bd5e7-151">路徑是由一系列以 '/' 分隔的區段所組成，每個區段都可以有常值、以 {大括弧} ) 撰寫 (變數名稱，或是以 ' ' ) 撰寫的萬用字元 (\* 。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-151">A path consists of a series of segments delimited by '/', each segment can have a literal value, a variable name (written in {curly braces}), or a wildcard (written as '\*').</span></span> <span data-ttu-id="bd5e7-152">在先前的範本中，"\weather\ 片段是一個常值，而 "{state}" 與 "{city}" 則是變數。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-152">In the previous template the "\weather\ segment is a literal value while "{state}" and "{city}" are variables.</span></span> <span data-ttu-id="bd5e7-153">變數會從其大括弧的內容取得其名稱，之後可以用具體值取代，以建立 *關閉的 URI*。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-153">Variables take their name from the contents of their curly braces and they can later be replaced with a concrete value to create a *closed URI*.</span></span> <span data-ttu-id="bd5e7-154">萬用字元是選擇性的，但只能出現在 URI 的結尾，在邏輯上會符合「路徑的其餘部分」。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-154">The wildcard is optional, but can only appear at the end of the URI, where it logically matches "the rest of the path".</span></span>  
  
 <span data-ttu-id="bd5e7-155">查詢運算式（如果有的話）會指定一系列以 ' & ' 分隔的未排序名稱/值配對。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-155">The query expression, if present, specifies a series of unordered name/value pairs delimited by '&'.</span></span> <span data-ttu-id="bd5e7-156">查詢運算式的項目可以是一組常值 (x=2) 或是一組變數 (x={var})。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-156">Elements of the query expression can either be literal pairs (x=2) or a variable pair (x={var}).</span></span> <span data-ttu-id="bd5e7-157">只有查詢運算式的右側才可以放置變數運算式。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-157">Only the right side of the query can have a variable expression.</span></span> <span data-ttu-id="bd5e7-158">不允許 ({someName} = {someValue}。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-158">({someName} = {someValue} is not allowed.</span></span> <span data-ttu-id="bd5e7-159">不允許使用未成對的值 (?x)。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-159">Unpaired values (?x) are not permitted.</span></span> <span data-ttu-id="bd5e7-160">空的查詢運算式和只包含單一 '？ ' 的查詢運算式之間沒有任何差異 (兩者均表示「任何查詢」 ) 。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-160">There is no difference between an empty query expression and a query expression consisting of just a single '?' (both mean "any query").</span></span>  
  
 <span data-ttu-id="bd5e7-161">片段運算式可能包含一個常值，不允許使用任何變數。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-161">The fragment expression can consist of a literal value, no variables are allowed.</span></span>  
  
 <span data-ttu-id="bd5e7-162">範本字串中所有的範本變數名稱必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-162">All template variable names within a template string must be unique.</span></span> <span data-ttu-id="bd5e7-163">範本變數名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-163">Template variable names are case-insensitive.</span></span>  
  
 <span data-ttu-id="bd5e7-164">有效的範本字串範例包括：</span><span class="sxs-lookup"><span data-stu-id="bd5e7-164">Examples of valid template strings:</span></span>  
  
- <span data-ttu-id="bd5e7-165">""</span><span class="sxs-lookup"><span data-stu-id="bd5e7-165">""</span></span>  
  
- <span data-ttu-id="bd5e7-166">"/shoe"</span><span class="sxs-lookup"><span data-stu-id="bd5e7-166">"/shoe"</span></span>  
  
- <span data-ttu-id="bd5e7-167">"/shoe/ \* "</span><span class="sxs-lookup"><span data-stu-id="bd5e7-167">"/shoe/\*"</span></span>  
  
- <span data-ttu-id="bd5e7-168">"{shoe}/boat"</span><span class="sxs-lookup"><span data-stu-id="bd5e7-168">"{shoe}/boat"</span></span>  
  
- <span data-ttu-id="bd5e7-169">"{鞋}/{boat}/bed/{quilt}"</span><span class="sxs-lookup"><span data-stu-id="bd5e7-169">"{shoe}/{boat}/bed/{quilt}"</span></span>  
  
- <span data-ttu-id="bd5e7-170">"鞋/{船}"</span><span class="sxs-lookup"><span data-stu-id="bd5e7-170">"shoe/{boat}"</span></span>  
  
- <span data-ttu-id="bd5e7-171">"鞋/{船}/ \* "</span><span class="sxs-lookup"><span data-stu-id="bd5e7-171">"shoe/{boat}/\*"</span></span>  
  
- <span data-ttu-id="bd5e7-172">「鞋/船？ x = 2」</span><span class="sxs-lookup"><span data-stu-id="bd5e7-172">"shoe/boat?x=2"</span></span>  
  
- <span data-ttu-id="bd5e7-173">"鞋/{船}？ x = {床}"</span><span class="sxs-lookup"><span data-stu-id="bd5e7-173">"shoe/{boat}?x={bed}"</span></span>  
  
- <span data-ttu-id="bd5e7-174">"鞋/{船}？ x = {床} &y = 波段"</span><span class="sxs-lookup"><span data-stu-id="bd5e7-174">"shoe/{boat}?x={bed}&y=band"</span></span>  
  
- <span data-ttu-id="bd5e7-175">"？ x = {鞋}"</span><span class="sxs-lookup"><span data-stu-id="bd5e7-175">"?x={shoe}"</span></span>  
  
- <span data-ttu-id="bd5e7-176">"鞋？ x = 3&y = {var}</span><span class="sxs-lookup"><span data-stu-id="bd5e7-176">"shoe?x=3&y={var}</span></span>  
  
 <span data-ttu-id="bd5e7-177">無效的範本字串範例包括：</span><span class="sxs-lookup"><span data-stu-id="bd5e7-177">Examples of invalid template strings:</span></span>  
  
- <span data-ttu-id="bd5e7-178">"{鞋}/{SHOE}/x = 2" –重複的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-178">"{shoe}/{SHOE}/x=2" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="bd5e7-179">"{鞋}/boat/？床 = {鞋}" –重複的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-179">"{shoe}/boat/?bed={shoe}" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="bd5e7-180">"？ x = 2&x = 3" –查詢字串內的名稱/值組必須是唯一的，即使它們是常值也是一樣。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-180">"?x=2&x=3" – Name/value pairs within a query string must be unique, even if they are literals.</span></span>  
  
- <span data-ttu-id="bd5e7-181">"？ x = 2&" –查詢字串的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-181">"?x=2&" – Query string is malformed.</span></span>  
  
- <span data-ttu-id="bd5e7-182">"？ 2&x = {鞋}" –查詢字串必須是成對的名稱/值。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-182">"?2&x={shoe}" – Query string must be name/value pairs.</span></span>  
  
- <span data-ttu-id="bd5e7-183">"？ y = 2&&X = 3" –查詢字串必須是名稱值組，名稱開頭不能是 ' & '。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-183">"?y=2&&X=3" – Query string must be name value pairs, names cannot start with '&'.</span></span>  
  
### <a name="compound-path-segments"></a><span data-ttu-id="bd5e7-184">複合路徑片段</span><span class="sxs-lookup"><span data-stu-id="bd5e7-184">Compound Path Segments</span></span>  

 <span data-ttu-id="bd5e7-185">複合路徑片段可以在單一 URI 路徑片段中包含多個變數以及與加入常值的變數。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-185">Compound path segments allow a single URI path segment to contain multiple variables as well as variables combined with literals.</span></span> <span data-ttu-id="bd5e7-186">以下範例列出有效的複合路徑片段：</span><span class="sxs-lookup"><span data-stu-id="bd5e7-186">The following are examples of valid compound path segments.</span></span>  
  
- <span data-ttu-id="bd5e7-187">/filename.{ext}/</span><span class="sxs-lookup"><span data-stu-id="bd5e7-187">/filename.{ext}/</span></span>  
  
- <span data-ttu-id="bd5e7-188">/{filename}.jpg/</span><span class="sxs-lookup"><span data-stu-id="bd5e7-188">/{filename}.jpg/</span></span>  
  
- <span data-ttu-id="bd5e7-189">/{filename}.{ext}/</span><span class="sxs-lookup"><span data-stu-id="bd5e7-189">/{filename}.{ext}/</span></span>  
  
- <span data-ttu-id="bd5e7-190">/{a}.{b}someLiteral{c}({d})/</span><span class="sxs-lookup"><span data-stu-id="bd5e7-190">/{a}.{b}someLiteral{c}({d})/</span></span>  
  
 <span data-ttu-id="bd5e7-191">以下範例列出無效的路徑片段：</span><span class="sxs-lookup"><span data-stu-id="bd5e7-191">The following are examples of invalid path segments.</span></span>  
  
- <span data-ttu-id="bd5e7-192">{}變數必須命名為。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-192">/{} - Variables must be named.</span></span>  
  
- <span data-ttu-id="bd5e7-193">/{shoe}{boat}：變數之間必須以常值分隔。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-193">/{shoe}{boat} - Variables must be separated by a literal.</span></span>  
  
### <a name="matching-and-compound-path-segments"></a><span data-ttu-id="bd5e7-194">比對和複合路徑區段</span><span class="sxs-lookup"><span data-stu-id="bd5e7-194">Matching and Compound Path Segments</span></span>  

 <span data-ttu-id="bd5e7-195">複合路徑區段可讓您定義一個 UriTemplate，該 UriTemplate 在單一路徑區段中有多個變數。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-195">Compound path segments allow you to define a UriTemplate that has multiple variables within a single path segment.</span></span> <span data-ttu-id="bd5e7-196">例如，在下列範本字串中： "Addresses/{state}。{city} "兩個變數 (州和城市) 是在相同的區段中定義。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-196">For example, in the following template string: "Addresses/{state}.{city}" two variables (state and city) are defined within the same segment.</span></span> <span data-ttu-id="bd5e7-197">此範本會比對類似的 URL， `http://example.com/Washington.Redmond` 但它也會比對類似的 url `http://example.com/Washington.Redmond.Microsoft` 。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-197">This template would match a URL such as `http://example.com/Washington.Redmond` but it will also match an URL like `http://example.com/Washington.Redmond.Microsoft`.</span></span> <span data-ttu-id="bd5e7-198">在後者的情況下，狀態變數將會包含 "華盛頓"，且 city 變數將會包含 "Redmond. Microsoft"。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-198">In the latter case, the state variable will contain "Washington" and the city variable will contain "Redmond.Microsoft".</span></span> <span data-ttu-id="bd5e7-199">在此情況下，任何文字 (除了 ‘/’ 之外) 都會比對 {city} 變數。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-199">In this case any text (except ‘/’) will match the {city} variable.</span></span> <span data-ttu-id="bd5e7-200">如果您想要將不符合「額外」文字的範本，請將變數放在個別的範本區段中，例如： "Addresses/{state}/{city}。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-200">If you want a template that will not match the "extra" text, place the variable in a separate template segment, for example: "Addresses/{state}/{city}.</span></span>  
  
### <a name="named-wildcard-segments"></a><span data-ttu-id="bd5e7-201">命名的萬用字元片段</span><span class="sxs-lookup"><span data-stu-id="bd5e7-201">Named Wildcard Segments</span></span>  

 <span data-ttu-id="bd5e7-202">名為萬用字元區段的任何路徑變數區段，其變數名稱的開頭都是萬用字元 ' \* '。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-202">A named wildcard segment is any path variable segment whose variable name begins with the wildcard character ‘\*’.</span></span> <span data-ttu-id="bd5e7-203">下列範本字串包含了命名的萬用字元片段，名為 "shoe"。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-203">The following template string contains a named wildcard segment named "shoe".</span></span>  
  
`"literal/{*shoe}"`  
  
 <span data-ttu-id="bd5e7-204">萬用字元片段必須遵照下列規則：</span><span class="sxs-lookup"><span data-stu-id="bd5e7-204">Wildcard segments must follow the following rules:</span></span>  
  
- <span data-ttu-id="bd5e7-205">每一個範本字串最多只能使用一個萬用字元片段命名。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-205">There can be at most one named wildcard segment for each template string.</span></span>  
  
- <span data-ttu-id="bd5e7-206">命名的萬用字元片段必須置於路徑最右邊的片段中。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-206">A named wildcard segment must appear at the right-most segment in the path.</span></span>  
  
- <span data-ttu-id="bd5e7-207">在同一個範本字串中，不能同時使用命名的萬用字元片段以及匿名的萬用字元片段。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-207">A named wildcard segment cannot coexist with an anonymous wildcard segment within the same template string.</span></span>  
  
- <span data-ttu-id="bd5e7-208">命名的萬用字元片段名稱必須是獨一無二的。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-208">The name of a named wildcard segment must be unique.</span></span>  
  
- <span data-ttu-id="bd5e7-209">命名的萬用字元片段無法設定其預設值。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-209">Named wildcard segments cannot have default values.</span></span>  
  
- <span data-ttu-id="bd5e7-210">命名的萬用字元區段不能以 "/" 結尾。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-210">Named wildcard segments cannot end with "/".</span></span>  
  
### <a name="default-variable-values"></a><span data-ttu-id="bd5e7-211">預設變數值</span><span class="sxs-lookup"><span data-stu-id="bd5e7-211">Default Variable Values</span></span>  

 <span data-ttu-id="bd5e7-212">預設變數值可以讓指定要在範本內使用的變數預設值。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-212">Default variable values allow you to specify default values for variables within a template.</span></span> <span data-ttu-id="bd5e7-213">預設變數可以利用大括號指定，在其中宣告變數或是要傳遞給 UriTemplate 建構函式的集合。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-213">Default variables can be specified with the curly braces that declare the variable or as a collection passed to the UriTemplate constructor.</span></span> <span data-ttu-id="bd5e7-214">以下範例示範兩種利用預設變數值指定 <xref:System.UriTemplate>的方法。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-214">The following template shows two ways to specify a <xref:System.UriTemplate> with variables with default values.</span></span>  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 <span data-ttu-id="bd5e7-215">此範本宣告了預設值為 `a` 的具名變數 `1`，以及預設值為 `b`的具名變數 `5`。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-215">This template declares a variable named `a` with a default value of `1` and a variable named `b` with a default value of `5`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd5e7-216">只有路徑片段變數才能有預設值。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-216">Only path segment variables are allowed to have default values.</span></span> <span data-ttu-id="bd5e7-217">查詢字串變數、複合片段變數以及命名的萬用字元變數，都不能有預設值。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-217">Query string variables, compound segment variables, and named wildcard variables are not permitted to have default values.</span></span>  
  
 <span data-ttu-id="bd5e7-218">下列程式碼示範進行候選 URI 比對時，會如何處理預設變數。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-218">The following code shows how default variable values are handled when matching a candidate URI.</span></span>  
  
```csharp
Uri baseAddress = new Uri("http://localhost:8000/");

UriTemplate t = new UriTemplate("/{state=WA}/{city=Redmond}/", true);
Uri candidate = new Uri("http://localhost:8000/OR");

UriTemplateMatch m1 = t.Match(baseAddress, candidate);

Console.WriteLine($"Template: {t}");
Console.WriteLine($"Candidate URI: {candidate}");

// Display contents of BoundVariables
Console.WriteLine("BoundVariables:");
foreach (string key in m1.BoundVariables.AllKeys)
{
    Console.WriteLine($"\t{key}={m1.BoundVariables[key]}");
}
// The output of the above code is  
// Template: /{state=WA}/{city=Redmond}/
// Candidate URI: http://localhost:8000/OR
// BoundVariables:
//         STATE=OR
//         CITY=Redmond
```  
  
> [!NOTE]
> <span data-ttu-id="bd5e7-219">URI （例如）不 `http://localhost:8000///` 符合上述程式碼中所列的範本，不過 uri （例如） `http://localhost:8000/` 。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-219">A URI such as `http://localhost:8000///` does not match the template listed in the preceding code, however a URI such as `http://localhost:8000/` does.</span></span>  
  
 <span data-ttu-id="bd5e7-220">下列程式碼示範以範例建立 URI 比對時，會如何處理預設變數。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-220">The following code shows how default variable values are handled when creating a URI with a template.</span></span>  
  
```csharp
Uri baseAddress = new Uri("http://localhost:8000/");  
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);  
NameValueCollection vals = new NameValueCollection();  
vals.Add("a", "10");  
  
Uri boundUri = t.BindByName(baseAddress, vals);  
Console.WriteLine("BaseAddress: {0}", baseAddress);  
Console.WriteLine("Template: {0}", t.ToString());  
  
Console.WriteLine("Values: ");  
foreach (string key in vals.AllKeys)  
{  
    Console.WriteLine("\tKey = {0}, Value = {1}", key, vals[key]);  
}  
Console.WriteLine("Bound URI: {0}", boundUri);  
  
// The output of the preceding code is  
// BaseAddress: http://localhost:8000/  
// Template: /test/{a}/{b}  
// Values:  
//     Key = a, Value = 10  
// Bound URI: http://localhost:8000/test/10/5  
```  
  
<span data-ttu-id="bd5e7-221">如果某一個變數指定的預設值為 `null`，則會使用其他幾項條件約束。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-221">When a variable is given a default value of `null` there are some additional constraints.</span></span> <span data-ttu-id="bd5e7-222">如果變數置於範本字串最右邊的片段中，或是片段所有的右邊片段都有 `null` 做為預設值，變數的預設值才可以設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-222">A variable can have a default value of `null` if the variable is contained within the right most segment of the template string or if all segments to the right of the segment have default values of `null`.</span></span> <span data-ttu-id="bd5e7-223">下列是預設值為 `null`的有效範本字串：</span><span class="sxs-lookup"><span data-stu-id="bd5e7-223">The following are valid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 <span data-ttu-id="bd5e7-224">下列是預設值為的無效範本字串 `null` ：</span><span class="sxs-lookup"><span data-stu-id="bd5e7-224">The following are invalid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a><span data-ttu-id="bd5e7-225">預設值與進行比對</span><span class="sxs-lookup"><span data-stu-id="bd5e7-225">Default Values and Matching</span></span>  

 <span data-ttu-id="bd5e7-226">將候選 URI 與一個有預設值的範本進行比對時，如果候選 URI 內沒有指定值，預設值會置於 <xref:System.UriTemplateMatch.BoundVariables%2A> 集合中。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-226">When matching a candidate URI with a template that has default values, the default values are placed in the <xref:System.UriTemplateMatch.BoundVariables%2A> collection if values are not specified in the candidate URI.</span></span>  
  
### <a name="template-equivalence"></a><span data-ttu-id="bd5e7-227">相等的範本</span><span class="sxs-lookup"><span data-stu-id="bd5e7-227">Template Equivalence</span></span>  

 <span data-ttu-id="bd5e7-228">當所有範本的常值相符，而且它們在相同的區段中具有變數時，兩個樣板即為 *結構相等* 的範本。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-228">Two templates are said to be *structurally equivalent* when all of the templates' literals match and they have variables in the same segments.</span></span> <span data-ttu-id="bd5e7-229">例如，下列範本在結構上是相等的：</span><span class="sxs-lookup"><span data-stu-id="bd5e7-229">For example the following templates are structurally equivalent:</span></span>  
  
- <span data-ttu-id="bd5e7-230">/a/{var1}/b b/{var2}？ x = 1&y = 2</span><span class="sxs-lookup"><span data-stu-id="bd5e7-230">/a/{var1}/b b/{var2}?x=1&y=2</span></span>  
  
- <span data-ttu-id="bd5e7-231">a/{x}/b% 20b/{var1}？ y = 2&x = 1</span><span class="sxs-lookup"><span data-stu-id="bd5e7-231">a/{x}/b%20b/{var1}?y=2&x=1</span></span>  
  
- <span data-ttu-id="bd5e7-232">a/{y}/B% 20B/{z}/？ y = 2&x = 1</span><span class="sxs-lookup"><span data-stu-id="bd5e7-232">a/{y}/B%20B/{z}/?y=2&x=1</span></span>  
  
 <span data-ttu-id="bd5e7-233">請注意下列幾點事項：</span><span class="sxs-lookup"><span data-stu-id="bd5e7-233">A few things to notice:</span></span>  
  
- <span data-ttu-id="bd5e7-234">如果範本包含好幾條前置斜線，則只會忽略第一條斜線。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-234">If a template contains leading slashes, only the first one is ignored.</span></span>  
  
- <span data-ttu-id="bd5e7-235">在您比較範本字串中的結構相等性時，可忽略變數名稱的大小寫，但須注意路徑片段與查詢字串的大小寫。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-235">When comparing template strings for structural equivalence, case is ignored for variable names and path segments, query strings are case sensitive.</span></span>  
  
- <span data-ttu-id="bd5e7-236">查詢字串尚未排序。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-236">Query strings are unordered.</span></span>  
  
## <a name="uritemplatetable"></a><span data-ttu-id="bd5e7-237">UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="bd5e7-237">UriTemplateTable</span></span>  

 <span data-ttu-id="bd5e7-238"><xref:System.UriTemplateTable> 類別代表 <xref:System.UriTemplate> 物件的關聯表，而此物件則是繫結至開發人員所選擇之物件。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-238">The <xref:System.UriTemplateTable> class represents an associative table of <xref:System.UriTemplate> objects bound to an object of the developer's choosing.</span></span> <span data-ttu-id="bd5e7-239"><xref:System.UriTemplateTable> 至少必須包含一個 <xref:System.UriTemplate>，才能呼叫 <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-239">A <xref:System.UriTemplateTable> must contain at least one <xref:System.UriTemplate> prior to calling <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span> <span data-ttu-id="bd5e7-240"><xref:System.UriTemplateTable> 的內容會等到呼叫 <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> 之後才變更。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-240">The contents of a <xref:System.UriTemplateTable> can be changed until <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="bd5e7-241">呼叫 <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> 時會執行驗證。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-241">Validation is performed when <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="bd5e7-242">執行的驗證類型需視 `allowMultiple` 的 <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> 參數值而定。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-242">The type of validation performed depends upon the value of the `allowMultiple` parameter to <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span>  
  
 <span data-ttu-id="bd5e7-243">當呼叫 <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> 並傳入 `false` 時，<xref:System.UriTemplateTable> 會進行檢查以確定表中沒有任何範本。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-243">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `false`, the <xref:System.UriTemplateTable> checks to make sure there are no templates in the table.</span></span> <span data-ttu-id="bd5e7-244">如果它找到任何結構上相等的範本，就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-244">If it finds any structurally equivalent templates, it throws an exception.</span></span> <span data-ttu-id="bd5e7-245">當您希望確定只有一個範本符合傳入的 URI 時，就可以使用這個方法來搭配 <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29>。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-245">This is used in conjunction with <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> when you want to ensure only one template matches an incoming URI.</span></span>  
  
 <span data-ttu-id="bd5e7-246">當呼叫 <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> 並傳入 `true` 時，<xref:System.UriTemplateTable> 允許多個結構上相等的範本包含在 <xref:System.UriTemplateTable> 中。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-246">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `true`, <xref:System.UriTemplateTable> allows multiple, structurally-equivalent templates to be contained within a <xref:System.UriTemplateTable>.</span></span>  
  
 <span data-ttu-id="bd5e7-247">如果將一組 <xref:System.UriTemplate> 物件新增到 <xref:System.UriTemplateTable> 包含查詢字串中，則不得使用語意模糊的字串。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-247">If a set of <xref:System.UriTemplate> objects added to a <xref:System.UriTemplateTable> contain query strings they must not be ambiguous.</span></span> <span data-ttu-id="bd5e7-248">您可以使用相同的查詢字串。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-248">Identical query strings are allowed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd5e7-249">雖然 <xref:System.UriTemplateTable> 允許使用 HTTP 以外的配置做為基底位址，但是在進行候選 URI 與範本比對時，仍然會忽略置及連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-249">While the <xref:System.UriTemplateTable> allows base addresses that use schemes other than HTTP, the scheme and port number are ignored when matching candidate URIs to templates.</span></span>  
  
### <a name="query-string-ambiguity"></a><span data-ttu-id="bd5e7-250">查詢字串模稜兩可</span><span class="sxs-lookup"><span data-stu-id="bd5e7-250">Query String Ambiguity</span></span>  

 <span data-ttu-id="bd5e7-251">如果有一個 URI 同時符合多個範本，則共用相同路徑的範本會包含語意模糊的查詢字串。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-251">Templates that share an equivalent path contain ambiguous query strings if there is a URI that matches more than one template.</span></span>  
  
 <span data-ttu-id="bd5e7-252">下列查詢字串組本身語意都很明確：</span><span class="sxs-lookup"><span data-stu-id="bd5e7-252">The following sets of query strings are unambiguous within themselves:</span></span>  
  
- <span data-ttu-id="bd5e7-253">?x=1</span><span class="sxs-lookup"><span data-stu-id="bd5e7-253">?x=1</span></span>  
  
- <span data-ttu-id="bd5e7-254">?x=2</span><span class="sxs-lookup"><span data-stu-id="bd5e7-254">?x=2</span></span>  
  
- <span data-ttu-id="bd5e7-255">?x=3</span><span class="sxs-lookup"><span data-stu-id="bd5e7-255">?x=3</span></span>  
  
- <span data-ttu-id="bd5e7-256">？ x = 1&y = {var}</span><span class="sxs-lookup"><span data-stu-id="bd5e7-256">?x=1&y={var}</span></span>  
  
- <span data-ttu-id="bd5e7-257">？ x = 2&z = {var}</span><span class="sxs-lookup"><span data-stu-id="bd5e7-257">?x=2&z={var}</span></span>  
  
- <span data-ttu-id="bd5e7-258">?x=3</span><span class="sxs-lookup"><span data-stu-id="bd5e7-258">?x=3</span></span>  
  
- <span data-ttu-id="bd5e7-259">?x=1</span><span class="sxs-lookup"><span data-stu-id="bd5e7-259">?x=1</span></span>  
  
- <span data-ttu-id="bd5e7-260">?</span><span class="sxs-lookup"><span data-stu-id="bd5e7-260">?</span></span>  
  
- <span data-ttu-id="bd5e7-261">?</span><span class="sxs-lookup"><span data-stu-id="bd5e7-261">?</span></span> <span data-ttu-id="bd5e7-262">x={var}</span><span class="sxs-lookup"><span data-stu-id="bd5e7-262">x={var}</span></span>  
  
- <span data-ttu-id="bd5e7-263">?</span><span class="sxs-lookup"><span data-stu-id="bd5e7-263">?</span></span>  
  
- <span data-ttu-id="bd5e7-264">？ m = get&c = rss</span><span class="sxs-lookup"><span data-stu-id="bd5e7-264">?m=get&c=rss</span></span>  
  
- <span data-ttu-id="bd5e7-265">？ m = put&c = rss</span><span class="sxs-lookup"><span data-stu-id="bd5e7-265">?m=put&c=rss</span></span>  
  
- <span data-ttu-id="bd5e7-266">？ m = get&c = atom</span><span class="sxs-lookup"><span data-stu-id="bd5e7-266">?m=get&c=atom</span></span>  
  
- <span data-ttu-id="bd5e7-267">？ m = put&c = atom</span><span class="sxs-lookup"><span data-stu-id="bd5e7-267">?m=put&c=atom</span></span>  
  
 <span data-ttu-id="bd5e7-268">下列查詢字串範本組本身語意都很模糊：</span><span class="sxs-lookup"><span data-stu-id="bd5e7-268">The following sets of query string templates are ambiguous within themselves:</span></span>  
  
- <span data-ttu-id="bd5e7-269">?x=1</span><span class="sxs-lookup"><span data-stu-id="bd5e7-269">?x=1</span></span>  
  
- <span data-ttu-id="bd5e7-270">?x={var}</span><span class="sxs-lookup"><span data-stu-id="bd5e7-270">?x={var}</span></span>  
  
 <span data-ttu-id="bd5e7-271">"x=1"：與兩個範本相符。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-271">"x=1" - Matches both templates.</span></span>  
  
- <span data-ttu-id="bd5e7-272">?x=1</span><span class="sxs-lookup"><span data-stu-id="bd5e7-272">?x=1</span></span>  
  
- <span data-ttu-id="bd5e7-273">?y=2</span><span class="sxs-lookup"><span data-stu-id="bd5e7-273">?y=2</span></span>  
  
 <span data-ttu-id="bd5e7-274">"x = 1&y = 2" 符合兩個範本。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-274">"x=1&y=2" matches both templates.</span></span> <span data-ttu-id="bd5e7-275">這是因為查詢字串所包含的查詢字串變數數量可能超出範本所符合的查詢字串變數數量。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-275">This is because a query string may contain more query string variables then the template it matches.</span></span>  
  
- <span data-ttu-id="bd5e7-276">?x=1</span><span class="sxs-lookup"><span data-stu-id="bd5e7-276">?x=1</span></span>  
  
- <span data-ttu-id="bd5e7-277">？ x = 1&y = {var}</span><span class="sxs-lookup"><span data-stu-id="bd5e7-277">?x=1&y={var}</span></span>  
  
 <span data-ttu-id="bd5e7-278">"x = 1&y = 3" 符合兩個範本。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-278">"x=1&y=3" matches both templates.</span></span>  
  
- <span data-ttu-id="bd5e7-279">？ x = 3&y = 4</span><span class="sxs-lookup"><span data-stu-id="bd5e7-279">?x=3&y=4</span></span>  
  
- <span data-ttu-id="bd5e7-280">？ x = 3&z = 5</span><span class="sxs-lookup"><span data-stu-id="bd5e7-280">?x=3&z=5</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd5e7-281">當字元 á 與 Á 出現在 URI 路徑或 <xref:System.UriTemplate> 路徑片段常值中時，兩者將被視為不同的字元 (但是字元 a 與 A 則被視為相同)。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-281">The characters á and Á are considered to be different characters when they appear as part of a URI path or <xref:System.UriTemplate> path segment literal (but the characters a and A are considered to be the same).</span></span> <span data-ttu-id="bd5e7-282">當字元 á 與 Á 出現在 <xref:System.UriTemplate> {variableName} 或查詢字串中時，兩者將被視為相同的字元 (而且字元 a 與 A 亦將被視為相同)。</span><span class="sxs-lookup"><span data-stu-id="bd5e7-282">The characters á and Á are considered to be the same characters when they appear as part of a <xref:System.UriTemplate> {variableName} or a query string (and a and A are also considered to be the same characters).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd5e7-283">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd5e7-283">See also</span></span>

- [<span data-ttu-id="bd5e7-284">WCF Web HTTP 程式設計模型概觀</span><span class="sxs-lookup"><span data-stu-id="bd5e7-284">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="bd5e7-285">WCF Web HTTP 程式設計物件模型</span><span class="sxs-lookup"><span data-stu-id="bd5e7-285">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
- [<span data-ttu-id="bd5e7-286">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="bd5e7-286">UriTemplate</span></span>](../samples/uritemplate-sample.md)
- [<span data-ttu-id="bd5e7-287">UriTemplate 資料表</span><span class="sxs-lookup"><span data-stu-id="bd5e7-287">UriTemplate Table</span></span>](../samples/uritemplate-table-sample.md)
- [<span data-ttu-id="bd5e7-288">UriTemplate 資料表發送器</span><span class="sxs-lookup"><span data-stu-id="bd5e7-288">UriTemplate Table Dispatcher</span></span>](../samples/uritemplate-table-dispatcher-sample.md)
