---
title: UriTemplate 與 UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: 66463248f66457aa61ceea22afd003f7b93717e1
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47090509"
---
# <a name="uritemplate-and-uritemplatetable"></a><span data-ttu-id="2b764-102">UriTemplate 與 UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="2b764-102">UriTemplate and UriTemplateTable</span></span>
<span data-ttu-id="2b764-103">Web 開發人員需要能夠描述其服務所回應的 URI 形式與配置。</span><span class="sxs-lookup"><span data-stu-id="2b764-103">Web developers require the ability to describe the shape and layout of the URIs that their services respond to.</span></span> <span data-ttu-id="2b764-104">Windows Communication Foundation (WCF) 加入兩個新的類別，可讓開發人員充分掌控其 Uri。</span><span class="sxs-lookup"><span data-stu-id="2b764-104">Windows Communication Foundation (WCF) added two new classes to give developers control over their URIs.</span></span> <span data-ttu-id="2b764-105"><xref:System.UriTemplate> 和<xref:System.UriTemplateTable>WCF 中形成的 URI 為基礎的發送引擎基礎。</span><span class="sxs-lookup"><span data-stu-id="2b764-105"><xref:System.UriTemplate> and <xref:System.UriTemplateTable> form the basis of the URI-based dispatch engine in WCF.</span></span> <span data-ttu-id="2b764-106">這些類別也可用在其本身，可讓開發人員充分運用範本與 URI 對應機制不需實作 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="2b764-106">These classes can also be used on their own, allowing developers to take advantage of templates and the URI mapping mechanism without implementing a WCF service.</span></span>  
  
## <a name="templates"></a><span data-ttu-id="2b764-107">範本</span><span class="sxs-lookup"><span data-stu-id="2b764-107">Templates</span></span>  
 <span data-ttu-id="2b764-108">範本提供了一種用來描述相對 URI 集合的方式。</span><span class="sxs-lookup"><span data-stu-id="2b764-108">A template is a way to describe a set of relative URIs.</span></span> <span data-ttu-id="2b764-109">下表中的 URI 範本集將說明如何定義負責擷取各種氣象資訊型別的系統。</span><span class="sxs-lookup"><span data-stu-id="2b764-109">The set of URI templates in the following table shows how a system that retrieves various types of weather information might be defined.</span></span>  
  
|<span data-ttu-id="2b764-110">資料</span><span class="sxs-lookup"><span data-stu-id="2b764-110">Data</span></span>|<span data-ttu-id="2b764-111">範本</span><span class="sxs-lookup"><span data-stu-id="2b764-111">Template</span></span>|  
|----------|--------------|  
|<span data-ttu-id="2b764-112">國內趨勢預測</span><span class="sxs-lookup"><span data-stu-id="2b764-112">National Forecast</span></span>|<span data-ttu-id="2b764-113">weather/national</span><span class="sxs-lookup"><span data-stu-id="2b764-113">weather/national</span></span>|  
|<span data-ttu-id="2b764-114">各州趨勢預測</span><span class="sxs-lookup"><span data-stu-id="2b764-114">State Forecast</span></span>|<span data-ttu-id="2b764-115">weather/{state}</span><span class="sxs-lookup"><span data-stu-id="2b764-115">weather/{state}</span></span>|  
|<span data-ttu-id="2b764-116">城市趨勢預測</span><span class="sxs-lookup"><span data-stu-id="2b764-116">City Forecast</span></span>|<span data-ttu-id="2b764-117">weather/{state}/{city}</span><span class="sxs-lookup"><span data-stu-id="2b764-117">weather/{state}/{city}</span></span>|  
|<span data-ttu-id="2b764-118">活動趨勢預測</span><span class="sxs-lookup"><span data-stu-id="2b764-118">Activity Forecast</span></span>|<span data-ttu-id="2b764-119">weather/{state}/{city}/{activity}</span><span class="sxs-lookup"><span data-stu-id="2b764-119">weather/{state}/{city}/{activity}</span></span>|  
  
 <span data-ttu-id="2b764-120">這份表格說明結構上類似的 URI 集合。</span><span class="sxs-lookup"><span data-stu-id="2b764-120">This table describes a set of structurally similar URIs.</span></span> <span data-ttu-id="2b764-121">每個項目都是 URI 範本。</span><span class="sxs-lookup"><span data-stu-id="2b764-121">Each entry is a URI template.</span></span> <span data-ttu-id="2b764-122">大括號內的片段描述變數，</span><span class="sxs-lookup"><span data-stu-id="2b764-122">The segments in curly braces describe variables.</span></span> <span data-ttu-id="2b764-123">大括號外的片段則描述常值字串。</span><span class="sxs-lookup"><span data-stu-id="2b764-123">The segments not in curly braces describe literal strings.</span></span> <span data-ttu-id="2b764-124">WCF 範本類別可以讓開發人員需要將傳入的 URI，例如，"/ weather/wa/seattle/循環 」，並使其符合範本描述，"/weather/wa/seattle/cycling {state} / {city} / {活動}"。</span><span class="sxs-lookup"><span data-stu-id="2b764-124">The WCF template classes allow a developer to take an incoming URI, for example, "/weather/wa/seattle/cycling", and match it to a template that describes it, "/weather/{state}/{city}/{activity}".</span></span>  
  
## <a name="uritemplate"></a><span data-ttu-id="2b764-125">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="2b764-125">UriTemplate</span></span>  
 <span data-ttu-id="2b764-126"><xref:System.UriTemplate> 是一個會封裝 URI 範本的類別。</span><span class="sxs-lookup"><span data-stu-id="2b764-126"><xref:System.UriTemplate> is a class that encapsulates a URI template.</span></span> <span data-ttu-id="2b764-127">建構函式會包含用來定義範本的字串參數。</span><span class="sxs-lookup"><span data-stu-id="2b764-127">The constructor takes a string parameter that defines the template.</span></span> <span data-ttu-id="2b764-128">此字串會將範本包含在下一節中說明的格式裡。</span><span class="sxs-lookup"><span data-stu-id="2b764-128">This string contains the template in the format described in the next section.</span></span> <span data-ttu-id="2b764-129"><xref:System.UriTemplate> 類別所提供的方法可讓您將傳入的 URI 與範本進行比對、從範本產生 URI、擷取範本中使用的變數名稱集合，並判斷這兩個範本是否相等，然後傳回範本的字串。</span><span class="sxs-lookup"><span data-stu-id="2b764-129">The <xref:System.UriTemplate> class provides methods that allow you match an incoming URI to a template, generate a URI from a template, retrieve a collection of variable names used in the template, determine whether two templates are equivalent, and return the template's string.</span></span>  
  
 <span data-ttu-id="2b764-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> 包含基底位址與候選 URI，並嘗試將 URI 與範本進行比對。</span><span class="sxs-lookup"><span data-stu-id="2b764-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> takes a base address and a candidate URI and attempts to match the URI to the template.</span></span> <span data-ttu-id="2b764-131">如果比對成功，則會傳回 <xref:System.UriTemplateMatch> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="2b764-131">If the match is successful, a <xref:System.UriTemplateMatch> instance is returned.</span></span> <span data-ttu-id="2b764-132"><xref:System.UriTemplateMatch>物件包含一個起始 URI、一個候選 URI、一個查詢參數的名稱/值集合、一個相對路徑片段陣列、一個相符的變數名稱/值集合、用來執行比對的<xref:System.UriTemplate>執行個體、一個包含候選 URI (當範本包含萬用字元時所使用) 中任何不相符部分的字串，以及一個與範本相關聯的物件。</span><span class="sxs-lookup"><span data-stu-id="2b764-132">The <xref:System.UriTemplateMatch> object contains a base URI, the candidate URI, a name/value collection of the query parameters, an array of the relative path segments, a name/value collection of variables that were matched, the <xref:System.UriTemplate> instance used to perform the match, a string that contains any unmatched portion of the candidate URI (used when the template has a wildcard), and an object that is associated with the template.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b764-133"><xref:System.UriTemplate> 類別在將範本與候選 URI 與進行比較時，會忽略配置和連接埠編號。</span><span class="sxs-lookup"><span data-stu-id="2b764-133">The <xref:System.UriTemplate> class ignores the scheme and port number when matching a candidate URI to a template.</span></span>  
  
 <span data-ttu-id="2b764-134">有兩種方法可讓您從範本中產生 URI：<xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> 和 <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>。</span><span class="sxs-lookup"><span data-stu-id="2b764-134">There are two methods that allow you to generate a URI from a template, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> and <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span></span> <span data-ttu-id="2b764-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> 需要基底位址和參數的名稱/值集合。</span><span class="sxs-lookup"><span data-stu-id="2b764-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> takes a base address and a name/value collection of parameters.</span></span> <span data-ttu-id="2b764-136">當範本經過繫結，就會以這些參數來取代變數。</span><span class="sxs-lookup"><span data-stu-id="2b764-136">These parameters are substituted for variables when the template is bound.</span></span> <span data-ttu-id="2b764-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> 將會由左至右取代其接受的名稱/值組。</span><span class="sxs-lookup"><span data-stu-id="2b764-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> takes the name/value pairs and substitutes them left to right.</span></span>  
  
 <span data-ttu-id="2b764-138"><xref:System.UriTemplate.ToString> 會傳回範本字串。</span><span class="sxs-lookup"><span data-stu-id="2b764-138"><xref:System.UriTemplate.ToString> returns the template string.</span></span>  
  
 <span data-ttu-id="2b764-139"><xref:System.UriTemplate.PathSegmentVariableNames%2A> 屬性包含範本字串之路徑片段中所使用的變數名稱集合。</span><span class="sxs-lookup"><span data-stu-id="2b764-139">The <xref:System.UriTemplate.PathSegmentVariableNames%2A> property contains a collection of the names of the variables used within path segments in the template string.</span></span>  
  
 <span data-ttu-id="2b764-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> 以 <xref:System.UriTemplate> 做為參數，並傳回布林值指出兩個範本是否相等。</span><span class="sxs-lookup"><span data-stu-id="2b764-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> takes a <xref:System.UriTemplate> as a parameter and returns a Boolean value that specifies whether the two templates are equivalent.</span></span> <span data-ttu-id="2b764-141">如需詳細資訊，請參閱本主題稍後的相等的範本區段。</span><span class="sxs-lookup"><span data-stu-id="2b764-141">For more information, see the Template Equivalence section later in this topic.</span></span>  
  
 <span data-ttu-id="2b764-142"><xref:System.UriTemplate> 的設計即是可與符合 HTTP URI 文法的任何 URI 配置搭配使用。</span><span class="sxs-lookup"><span data-stu-id="2b764-142"><xref:System.UriTemplate> is designed to work with any URI scheme that conforms to the HTTP URI grammar.</span></span> <span data-ttu-id="2b764-143">以下是支援的 URI 配置範例：</span><span class="sxs-lookup"><span data-stu-id="2b764-143">The following are examples of supported URI schemes.</span></span>  
  
- <span data-ttu-id="2b764-144">http://</span><span class="sxs-lookup"><span data-stu-id="2b764-144">http://</span></span>  
  
- <span data-ttu-id="2b764-145">https://</span><span class="sxs-lookup"><span data-stu-id="2b764-145">https://</span></span>  
  
- <span data-ttu-id="2b764-146">net.tcp://</span><span class="sxs-lookup"><span data-stu-id="2b764-146">net.tcp://</span></span>  
  
- <span data-ttu-id="2b764-147">net.pipe://</span><span class="sxs-lookup"><span data-stu-id="2b764-147">net.pipe://</span></span>  
  
- <span data-ttu-id="2b764-148">sb://</span><span class="sxs-lookup"><span data-stu-id="2b764-148">sb://</span></span>  
  
 <span data-ttu-id="2b764-149">如 file:// 及 urn:// 的配置並不符合 HTTP URI 文法，若搭配 URI 範本使用，會造成無法預期的結果。</span><span class="sxs-lookup"><span data-stu-id="2b764-149">Schemes like file:// and urn:// do not conform to the HTTP URI grammar and cause unpredictable results when used with URI templates.</span></span>  
  
### <a name="template-string-syntax"></a><span data-ttu-id="2b764-150">範本字串語法</span><span class="sxs-lookup"><span data-stu-id="2b764-150">Template String Syntax</span></span>  
 <span data-ttu-id="2b764-151">範本包含三大部分：路徑、選擇性查詢以及選擇性片段。</span><span class="sxs-lookup"><span data-stu-id="2b764-151">A template has three parts: a path, an optional query, and an optional fragment.</span></span> <span data-ttu-id="2b764-152">例如，請參閱下列範本：</span><span class="sxs-lookup"><span data-stu-id="2b764-152">For an example, see the following template:</span></span>  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 <span data-ttu-id="2b764-153">路徑包含 "/weather/{state}/{city}"，查詢包含 "?forecast={length}，而片段則包含 "#frag1"。</span><span class="sxs-lookup"><span data-stu-id="2b764-153">The path consists of "/weather/{state}/{city}", the query consists of "?forecast={length}, and the fragment consists of "#frag1".</span></span>  
  
 <span data-ttu-id="2b764-154">路徑運算式中的前置與句尾斜線是選用的，</span><span class="sxs-lookup"><span data-stu-id="2b764-154">Leading and trailing slashes are optional in the path expression.</span></span> <span data-ttu-id="2b764-155">查詢與片段運算式可以全部省略掉。</span><span class="sxs-lookup"><span data-stu-id="2b764-155">Both the query and fragment expressions can be omitted entirely.</span></span> <span data-ttu-id="2b764-156">路徑包含一系列以分隔的區段 '/'，每個區段可以有常值、 變數名稱 （以大括號 {} 撰寫） 或萬用字元 (寫為\*')。</span><span class="sxs-lookup"><span data-stu-id="2b764-156">A path consists of a series of segments delimited by '/', each segment can have a literal value, a variable name (written in {curly braces}), or a wildcard (written as '\*').</span></span> <span data-ttu-id="2b764-157">在先前的範本中，"\weather\ 片段是一個常值，而 "{state}" 與 "{city}" 則是變數。</span><span class="sxs-lookup"><span data-stu-id="2b764-157">In the previous template the "\weather\ segment is a literal value while "{state}" and "{city}" are variables.</span></span> <span data-ttu-id="2b764-158">負責從其大括號的內容名稱，並稍後可以取代實體值來建立*關閉 URI*。</span><span class="sxs-lookup"><span data-stu-id="2b764-158">Variables take their name from the contents of their curly braces and they can later be replaced with a concrete value to create a *closed URI*.</span></span> <span data-ttu-id="2b764-159">萬用字元是選擇性的但只能出現在 URI，其中在邏輯上符合 「 其餘的路徑 」 的結尾。</span><span class="sxs-lookup"><span data-stu-id="2b764-159">The wildcard is optional, but can only appear at the end of the URI, where it logically matches "the rest of the path".</span></span>  
  
 <span data-ttu-id="2b764-160">查詢運算式 (如果有的話)，會指定一系列由 '&' 所分隔且未排序的名稱/值對。</span><span class="sxs-lookup"><span data-stu-id="2b764-160">The query expression, if present, specifies a series of unordered name/value pairs delimited by '&'.</span></span> <span data-ttu-id="2b764-161">查詢運算式的項目可以是一組常值 (x=2) 或是一組變數 (x={var})。</span><span class="sxs-lookup"><span data-stu-id="2b764-161">Elements of the query expression can either be literal pairs (x=2) or a variable pair (x={var}).</span></span> <span data-ttu-id="2b764-162">只有查詢運算式的右側才可以放置變數運算式。</span><span class="sxs-lookup"><span data-stu-id="2b764-162">Only the right side of the query can have a variable expression.</span></span> <span data-ttu-id="2b764-163">不允許 ({someName} = {someValue}。</span><span class="sxs-lookup"><span data-stu-id="2b764-163">({someName} = {someValue} is not allowed.</span></span> <span data-ttu-id="2b764-164">不允許使用未成對的值 (?x)。</span><span class="sxs-lookup"><span data-stu-id="2b764-164">Unpaired values (?x) are not permitted.</span></span> <span data-ttu-id="2b764-165">空的查詢運算式和單純包含一個查詢運算式之間沒有差異 '？ '（兩者都代表"any query"。）</span><span class="sxs-lookup"><span data-stu-id="2b764-165">There is no difference between an empty query expression and a query expression consisting of just a single '?' (both mean "any query").</span></span>  
  
 <span data-ttu-id="2b764-166">片段運算式可能包含一個常值，不允許使用任何變數。</span><span class="sxs-lookup"><span data-stu-id="2b764-166">The fragment expression can consist of a literal value, no variables are allowed.</span></span>  
  
 <span data-ttu-id="2b764-167">範本字串中所有的範本變數名稱必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="2b764-167">All template variable names within a template string must be unique.</span></span> <span data-ttu-id="2b764-168">範本變數名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="2b764-168">Template variable names are case-insensitive.</span></span>  
  
 <span data-ttu-id="2b764-169">有效的範本字串範例包括：</span><span class="sxs-lookup"><span data-stu-id="2b764-169">Examples of valid template strings:</span></span>  
  
- <span data-ttu-id="2b764-170">""</span><span class="sxs-lookup"><span data-stu-id="2b764-170">""</span></span>  
  
- <span data-ttu-id="2b764-171">"/shoe"</span><span class="sxs-lookup"><span data-stu-id="2b764-171">"/shoe"</span></span>  
  
- <span data-ttu-id="2b764-172">「 /shoe/\*"</span><span class="sxs-lookup"><span data-stu-id="2b764-172">"/shoe/\*"</span></span>  
  
- <span data-ttu-id="2b764-173">"{shoe}/boat"</span><span class="sxs-lookup"><span data-stu-id="2b764-173">"{shoe}/boat"</span></span>  
  
- <span data-ttu-id="2b764-174">"{shoe} / {划船} /bed/ {quilt}"</span><span class="sxs-lookup"><span data-stu-id="2b764-174">"{shoe}/{boat}/bed/{quilt}"</span></span>  
  
- <span data-ttu-id="2b764-175">"shoe / {划船}"</span><span class="sxs-lookup"><span data-stu-id="2b764-175">"shoe/{boat}"</span></span>  
  
- <span data-ttu-id="2b764-176">"shoe / {划船} /\*"</span><span class="sxs-lookup"><span data-stu-id="2b764-176">"shoe/{boat}/\*"</span></span>  
  
- <span data-ttu-id="2b764-177">"shoe/船隻？ x = 2"</span><span class="sxs-lookup"><span data-stu-id="2b764-177">"shoe/boat?x=2"</span></span>  
  
- <span data-ttu-id="2b764-178">"shoe / {划船}？ x = {平台}"</span><span class="sxs-lookup"><span data-stu-id="2b764-178">"shoe/{boat}?x={bed}"</span></span>  
  
- <span data-ttu-id="2b764-179">"shoe/{boat}?x={bed}&y=band"</span><span class="sxs-lookup"><span data-stu-id="2b764-179">"shoe/{boat}?x={bed}&y=band"</span></span>  
  
- <span data-ttu-id="2b764-180">"？ x = {shoe}"</span><span class="sxs-lookup"><span data-stu-id="2b764-180">"?x={shoe}"</span></span>  
  
- <span data-ttu-id="2b764-181">"shoe?x=3&y={var}</span><span class="sxs-lookup"><span data-stu-id="2b764-181">"shoe?x=3&y={var}</span></span>  
  
 <span data-ttu-id="2b764-182">無效的範本字串範例包括：</span><span class="sxs-lookup"><span data-stu-id="2b764-182">Examples of invalid template strings:</span></span>  
  
- <span data-ttu-id="2b764-183">"{shoe} / {SHOE} / x = 2 」 – 重複的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="2b764-183">"{shoe}/{SHOE}/x=2" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="2b764-184">"{shoe} /boat/？ bed = {shoe}"– 重複的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="2b764-184">"{shoe}/boat/?bed={shoe}" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="2b764-185">"？ x = 2&x = 3"– 名稱/值組的查詢字串內必須是唯一的即使它們是常值。</span><span class="sxs-lookup"><span data-stu-id="2b764-185">"?x=2&x=3" – Name/value pairs within a query string must be unique, even if they are literals.</span></span>  
  
- <span data-ttu-id="2b764-186">"？ x = 2 &"– 查詢字串的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="2b764-186">"?x=2&" – Query string is malformed.</span></span>  
  
- <span data-ttu-id="2b764-187">「？ 2 2&x = {shoe}"– 查詢字串必須是名稱/值組。</span><span class="sxs-lookup"><span data-stu-id="2b764-187">"?2&x={shoe}" – Query string must be name/value pairs.</span></span>  
  
- <span data-ttu-id="2b764-188">"？ y = 2 （& s) （& s) X = 3"– 查詢字串必須是名稱/值組，名稱不得以 '&'。</span><span class="sxs-lookup"><span data-stu-id="2b764-188">"?y=2&&X=3" – Query string must be name value pairs, names cannot start with '&'.</span></span>  
  
### <a name="compound-path-segments"></a><span data-ttu-id="2b764-189">複合路徑片段</span><span class="sxs-lookup"><span data-stu-id="2b764-189">Compound Path Segments</span></span>  
 <span data-ttu-id="2b764-190">複合路徑片段可以在單一 URI 路徑片段中包含多個變數以及與加入常值的變數。</span><span class="sxs-lookup"><span data-stu-id="2b764-190">Compound path segments allow a single URI path segment to contain multiple variables as well as variables combined with literals.</span></span> <span data-ttu-id="2b764-191">以下範例列出有效的複合路徑片段：</span><span class="sxs-lookup"><span data-stu-id="2b764-191">The following are examples of valid compound path segments.</span></span>  
  
- <span data-ttu-id="2b764-192">/filename.{ext}/</span><span class="sxs-lookup"><span data-stu-id="2b764-192">/filename.{ext}/</span></span>  
  
- <span data-ttu-id="2b764-193">/{filename}.jpg/</span><span class="sxs-lookup"><span data-stu-id="2b764-193">/{filename}.jpg/</span></span>  
  
- <span data-ttu-id="2b764-194">/{filename}.{ext}/</span><span class="sxs-lookup"><span data-stu-id="2b764-194">/{filename}.{ext}/</span></span>  
  
- <span data-ttu-id="2b764-195">/{a}.{b}someLiteral{c}({d})/</span><span class="sxs-lookup"><span data-stu-id="2b764-195">/{a}.{b}someLiteral{c}({d})/</span></span>  
  
 <span data-ttu-id="2b764-196">以下範例列出無效的路徑片段：</span><span class="sxs-lookup"><span data-stu-id="2b764-196">The following are examples of invalid path segments.</span></span>  
  
- <span data-ttu-id="2b764-197">/{} -變數必須命名。</span><span class="sxs-lookup"><span data-stu-id="2b764-197">/{} - Variables must be named.</span></span>  
  
- <span data-ttu-id="2b764-198">/{shoe}{boat}：變數之間必須以常值分隔。</span><span class="sxs-lookup"><span data-stu-id="2b764-198">/{shoe}{boat} - Variables must be separated by a literal.</span></span>  
  
### <a name="matching-and-compound-path-segments"></a><span data-ttu-id="2b764-199">比對和複合路徑區段</span><span class="sxs-lookup"><span data-stu-id="2b764-199">Matching and Compound Path Segments</span></span>  
 <span data-ttu-id="2b764-200">複合路徑區段可讓您定義一個 UriTemplate，該 UriTemplate 在單一路徑區段中有多個變數。</span><span class="sxs-lookup"><span data-stu-id="2b764-200">Compound path segments allow you to define a UriTemplate that has multiple variables within a single path segment.</span></span> <span data-ttu-id="2b764-201">例如，在下列範本字串: 「 位址 / {state}。{city}"的相同區段中定義兩個變數 （state 和 city）。</span><span class="sxs-lookup"><span data-stu-id="2b764-201">For example, in the following template string: "Addresses/{state}.{city}" two variables (state and city) are defined within the same segment.</span></span> <span data-ttu-id="2b764-202">此範本會比對 URL 這類`http://example.com/Washington.Redmond`，但它也會比對的 URL，例如`http://example.com/Washington.Redmond.Microsoft`。</span><span class="sxs-lookup"><span data-stu-id="2b764-202">This template would match a URL such as `http://example.com/Washington.Redmond` but it will also match an URL like `http://example.com/Washington.Redmond.Microsoft`.</span></span> <span data-ttu-id="2b764-203">在後者的情況下，狀態變數將包含 「 Washington 」，而 city 變數將包含"Redmond.Microsoft"。</span><span class="sxs-lookup"><span data-stu-id="2b764-203">In the latter case, the state variable will contain "Washington" and the city variable will contain "Redmond.Microsoft".</span></span> <span data-ttu-id="2b764-204">在此情況下，任何文字 (除了 ‘/’ 之外) 都會比對 {city} 變數。</span><span class="sxs-lookup"><span data-stu-id="2b764-204">In this case any text (except ‘/’) will match the {city} variable.</span></span> <span data-ttu-id="2b764-205">如果您想要使用範本不比對 「 額外的 」 文字，請將變數放在另一個範本區段中，例如: 「 位址 / {state} / {city}。</span><span class="sxs-lookup"><span data-stu-id="2b764-205">If you want a template that will not match the "extra" text, place the variable in a separate template segment, for example: "Addresses/{state}/{city}.</span></span>  
  
### <a name="named-wildcard-segments"></a><span data-ttu-id="2b764-206">命名的萬用字元片段</span><span class="sxs-lookup"><span data-stu-id="2b764-206">Named Wildcard Segments</span></span>  
 <span data-ttu-id="2b764-207">命名的萬用字元片段是任一路徑變數片段變數名稱開頭為萬用字元 '\*'。</span><span class="sxs-lookup"><span data-stu-id="2b764-207">A named wildcard segment is any path variable segment whose variable name begins with the wildcard character ‘\*’.</span></span> <span data-ttu-id="2b764-208">下列範本字串包含了命名的萬用字元片段，名為 "shoe"。</span><span class="sxs-lookup"><span data-stu-id="2b764-208">The following template string contains a named wildcard segment named "shoe".</span></span>  
  
```  
"literal/{*shoe}"  
```  
  
 <span data-ttu-id="2b764-209">萬用字元片段必須遵照下列規則：</span><span class="sxs-lookup"><span data-stu-id="2b764-209">Wildcard segments must follow the following rules:</span></span>  
  
- <span data-ttu-id="2b764-210">每一個範本字串最多只能使用一個萬用字元片段命名。</span><span class="sxs-lookup"><span data-stu-id="2b764-210">There can be at most one named wildcard segment for each template string.</span></span>  
  
- <span data-ttu-id="2b764-211">命名的萬用字元片段必須置於路徑最右邊的片段中。</span><span class="sxs-lookup"><span data-stu-id="2b764-211">A named wildcard segment must appear at the right-most segment in the path.</span></span>  
  
- <span data-ttu-id="2b764-212">在同一個範本字串中，不能同時使用命名的萬用字元片段以及匿名的萬用字元片段。</span><span class="sxs-lookup"><span data-stu-id="2b764-212">A named wildcard segment cannot coexist with an anonymous wildcard segment within the same template string.</span></span>  
  
- <span data-ttu-id="2b764-213">命名的萬用字元片段名稱必須是獨一無二的。</span><span class="sxs-lookup"><span data-stu-id="2b764-213">The name of a named wildcard segment must be unique.</span></span>  
  
- <span data-ttu-id="2b764-214">命名的萬用字元片段無法設定其預設值。</span><span class="sxs-lookup"><span data-stu-id="2b764-214">Named wildcard segments cannot have default values.</span></span>  
  
- <span data-ttu-id="2b764-215">命名的萬用字元片段結尾不可以"/"。</span><span class="sxs-lookup"><span data-stu-id="2b764-215">Named wildcard segments cannot end with "/".</span></span>  
  
### <a name="default-variable-values"></a><span data-ttu-id="2b764-216">預設變數值</span><span class="sxs-lookup"><span data-stu-id="2b764-216">Default Variable Values</span></span>  
 <span data-ttu-id="2b764-217">預設變數值可以讓指定要在範本內使用的變數預設值。</span><span class="sxs-lookup"><span data-stu-id="2b764-217">Default variable values allow you to specify default values for variables within a template.</span></span> <span data-ttu-id="2b764-218">預設變數可以利用大括號指定，在其中宣告變數或是要傳遞給 UriTemplate 建構函式的集合。</span><span class="sxs-lookup"><span data-stu-id="2b764-218">Default variables can be specified with the curly braces that declare the variable or as a collection passed to the UriTemplate constructor.</span></span> <span data-ttu-id="2b764-219">以下範例示範兩種利用預設變數值指定 <xref:System.UriTemplate>的方法。</span><span class="sxs-lookup"><span data-stu-id="2b764-219">The following template shows two ways to specify a <xref:System.UriTemplate> with variables with default values.</span></span>  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 <span data-ttu-id="2b764-220">此範本宣告了預設值為 `a` 的具名變數 `1`，以及預設值為 `b`的具名變數 `5`。</span><span class="sxs-lookup"><span data-stu-id="2b764-220">This template declares a variable named `a` with a default value of `1` and a variable named `b` with a default value of `5`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b764-221">只有路徑片段變數才能有預設值。</span><span class="sxs-lookup"><span data-stu-id="2b764-221">Only path segment variables are allowed to have default values.</span></span> <span data-ttu-id="2b764-222">查詢字串變數、複合片段變數以及命名的萬用字元變數，都不能有預設值。</span><span class="sxs-lookup"><span data-stu-id="2b764-222">Query string variables, compound segment variables, and named wildcard variables are not permitted to have default values.</span></span>  
  
 <span data-ttu-id="2b764-223">下列程式碼示範進行候選 URI 比對時，會如何處理預設變數。</span><span class="sxs-lookup"><span data-stu-id="2b764-223">The following code shows how default variable values are handled when matching a candidate URI.</span></span>  
  
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
> <span data-ttu-id="2b764-224">例如 URI`http://localhost:8000///`不符合上述的程式碼，不過所列的範本的 URI，例如`http://localhost:8000/`沒有。</span><span class="sxs-lookup"><span data-stu-id="2b764-224">A URI such as `http://localhost:8000///` does not match the template listed in the preceding code, however a URI such as `http://localhost:8000/` does.</span></span>  
  
 <span data-ttu-id="2b764-225">下列程式碼示範以範例建立 URI 比對時，會如何處理預設變數。</span><span class="sxs-lookup"><span data-stu-id="2b764-225">The following code shows how default variable values are handled when creating a URI with a template.</span></span>  
  
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
  
<span data-ttu-id="2b764-226">如果某一個變數指定的預設值為 `null`，則會使用其他幾項條件約束。</span><span class="sxs-lookup"><span data-stu-id="2b764-226">When a variable is given a default value of `null` there are some additional constraints.</span></span> <span data-ttu-id="2b764-227">如果變數置於範本字串最右邊的片段中，或是片段所有的右邊片段都有 `null` 做為預設值，變數的預設值才可以設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="2b764-227">A variable can have a default value of `null` if the variable is contained within the right most segment of the template string or if all segments to the right of the segment have default values of `null`.</span></span> <span data-ttu-id="2b764-228">下列是預設值為 `null`的有效範本字串：</span><span class="sxs-lookup"><span data-stu-id="2b764-228">The following are valid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 <span data-ttu-id="2b764-229">以下是無效的範本字串，預設值為`null`:</span><span class="sxs-lookup"><span data-stu-id="2b764-229">The following are invalid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a><span data-ttu-id="2b764-230">預設值與進行比對</span><span class="sxs-lookup"><span data-stu-id="2b764-230">Default Values and Matching</span></span>  
 <span data-ttu-id="2b764-231">將候選 URI 與一個有預設值的範本進行比對時，如果候選 URI 內沒有指定值，預設值會置於 <xref:System.UriTemplateMatch.BoundVariables%2A> 集合中。</span><span class="sxs-lookup"><span data-stu-id="2b764-231">When matching a candidate URI with a template that has default values, the default values are placed in the <xref:System.UriTemplateMatch.BoundVariables%2A> collection if values are not specified in the candidate URI.</span></span>  
  
### <a name="template-equivalence"></a><span data-ttu-id="2b764-232">相等的範本</span><span class="sxs-lookup"><span data-stu-id="2b764-232">Template Equivalence</span></span>  
 <span data-ttu-id="2b764-233">兩個範本都要*結構上相等*當所有範本的常值的比對，並它們有相同的區段中的變數。</span><span class="sxs-lookup"><span data-stu-id="2b764-233">Two templates are said to be *structurally equivalent* when all of the templates' literals match and they have variables in the same segments.</span></span> <span data-ttu-id="2b764-234">例如，下列範本在結構上是相等的：</span><span class="sxs-lookup"><span data-stu-id="2b764-234">For example the following templates are structurally equivalent:</span></span>  
  
- <span data-ttu-id="2b764-235">/a/{var1}/b b/{var2}?x=1&y=2</span><span class="sxs-lookup"><span data-stu-id="2b764-235">/a/{var1}/b b/{var2}?x=1&y=2</span></span>  
  
- <span data-ttu-id="2b764-236">a/{x}/b%20b/{var1}?y=2&x=1</span><span class="sxs-lookup"><span data-stu-id="2b764-236">a/{x}/b%20b/{var1}?y=2&x=1</span></span>  
  
- <span data-ttu-id="2b764-237">a/{y}/B%20B/{z}/?y=2&x=1</span><span class="sxs-lookup"><span data-stu-id="2b764-237">a/{y}/B%20B/{z}/?y=2&x=1</span></span>  
  
 <span data-ttu-id="2b764-238">請注意下列幾點事項：</span><span class="sxs-lookup"><span data-stu-id="2b764-238">A few things to notice:</span></span>  
  
- <span data-ttu-id="2b764-239">如果範本包含好幾條前置斜線，則只會忽略第一條斜線。</span><span class="sxs-lookup"><span data-stu-id="2b764-239">If a template contains leading slashes, only the first one is ignored.</span></span>  
  
- <span data-ttu-id="2b764-240">在您比較範本字串中的結構相等性時，可忽略變數名稱的大小寫，但須注意路徑片段與查詢字串的大小寫。</span><span class="sxs-lookup"><span data-stu-id="2b764-240">When comparing template strings for structural equivalence, case is ignored for variable names and path segments, query strings are case sensitive.</span></span>  
  
- <span data-ttu-id="2b764-241">查詢字串尚未排序。</span><span class="sxs-lookup"><span data-stu-id="2b764-241">Query strings are unordered.</span></span>  
  
## <a name="uritemplatetable"></a><span data-ttu-id="2b764-242">UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="2b764-242">UriTemplateTable</span></span>  
 <span data-ttu-id="2b764-243"><xref:System.UriTemplateTable> 類別代表 <xref:System.UriTemplate> 物件的關聯表，而此物件則是繫結至開發人員所選擇之物件。</span><span class="sxs-lookup"><span data-stu-id="2b764-243">The <xref:System.UriTemplateTable> class represents an associative table of <xref:System.UriTemplate> objects bound to an object of the developer's choosing.</span></span> <span data-ttu-id="2b764-244"><xref:System.UriTemplateTable> 至少必須包含一個 <xref:System.UriTemplate>，才能呼叫 <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>。</span><span class="sxs-lookup"><span data-stu-id="2b764-244">A <xref:System.UriTemplateTable> must contain at least one <xref:System.UriTemplate> prior to calling <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span> <span data-ttu-id="2b764-245"><xref:System.UriTemplateTable> 的內容會等到呼叫 <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> 之後才變更。</span><span class="sxs-lookup"><span data-stu-id="2b764-245">The contents of a <xref:System.UriTemplateTable> can be changed until <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="2b764-246">呼叫 <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> 時會執行驗證。</span><span class="sxs-lookup"><span data-stu-id="2b764-246">Validation is performed when <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="2b764-247">執行的驗證類型需視 `allowMultiple` 的 <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> 參數值而定。</span><span class="sxs-lookup"><span data-stu-id="2b764-247">The type of validation performed depends upon the value of the `allowMultiple` parameter to <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span>  
  
 <span data-ttu-id="2b764-248">當呼叫 <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> 並傳入 `false` 時，<xref:System.UriTemplateTable> 會進行檢查以確定表中沒有任何範本。</span><span class="sxs-lookup"><span data-stu-id="2b764-248">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `false`, the <xref:System.UriTemplateTable> checks to make sure there are no templates in the table.</span></span> <span data-ttu-id="2b764-249">如果它找到任何結構上相等的範本，就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2b764-249">If it finds any structurally equivalent templates, it throws an exception.</span></span> <span data-ttu-id="2b764-250">當您希望確定只有一個範本符合傳入的 URI 時，就可以使用這個方法來搭配 <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29>。</span><span class="sxs-lookup"><span data-stu-id="2b764-250">This is used in conjunction with <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> when you want to ensure only one template matches an incoming URI.</span></span>  
  
 <span data-ttu-id="2b764-251">當呼叫 <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> 並傳入 `true` 時，<xref:System.UriTemplateTable> 允許多個結構上相等的範本包含在 <xref:System.UriTemplateTable> 中。</span><span class="sxs-lookup"><span data-stu-id="2b764-251">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `true`, <xref:System.UriTemplateTable> allows multiple, structurally-equivalent templates to be contained within a <xref:System.UriTemplateTable>.</span></span>  
  
 <span data-ttu-id="2b764-252">如果將一組 <xref:System.UriTemplate> 物件新增到 <xref:System.UriTemplateTable> 包含查詢字串中，則不得使用語意模糊的字串。</span><span class="sxs-lookup"><span data-stu-id="2b764-252">If a set of <xref:System.UriTemplate> objects added to a <xref:System.UriTemplateTable> contain query strings they must not be ambiguous.</span></span> <span data-ttu-id="2b764-253">您可以使用相同的查詢字串。</span><span class="sxs-lookup"><span data-stu-id="2b764-253">Identical query strings are allowed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b764-254">雖然 <xref:System.UriTemplateTable> 允許使用 HTTP 以外的配置做為基底位址，但是在進行候選 URI 與範本比對時，仍然會忽略置及連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="2b764-254">While the <xref:System.UriTemplateTable> allows base addresses that use schemes other than HTTP, the scheme and port number are ignored when matching candidate URIs to templates.</span></span>  
  
### <a name="query-string-ambiguity"></a><span data-ttu-id="2b764-255">查詢字串模稜兩可</span><span class="sxs-lookup"><span data-stu-id="2b764-255">Query String Ambiguity</span></span>  
 <span data-ttu-id="2b764-256">如果有一個 URI 同時符合多個範本，則共用相同路徑的範本會包含語意模糊的查詢字串。</span><span class="sxs-lookup"><span data-stu-id="2b764-256">Templates that share an equivalent path contain ambiguous query strings if there is a URI that matches more than one template.</span></span>  
  
 <span data-ttu-id="2b764-257">下列查詢字串組本身語意都很明確：</span><span class="sxs-lookup"><span data-stu-id="2b764-257">The following sets of query strings are unambiguous within themselves:</span></span>  
  
- <span data-ttu-id="2b764-258">?x=1</span><span class="sxs-lookup"><span data-stu-id="2b764-258">?x=1</span></span>  
  
- <span data-ttu-id="2b764-259">?x=2</span><span class="sxs-lookup"><span data-stu-id="2b764-259">?x=2</span></span>  
  
- <span data-ttu-id="2b764-260">?x=3</span><span class="sxs-lookup"><span data-stu-id="2b764-260">?x=3</span></span>  
  
- <span data-ttu-id="2b764-261">?x=1&y={var}</span><span class="sxs-lookup"><span data-stu-id="2b764-261">?x=1&y={var}</span></span>  
  
- <span data-ttu-id="2b764-262">?x=2&z={var}</span><span class="sxs-lookup"><span data-stu-id="2b764-262">?x=2&z={var}</span></span>  
  
- <span data-ttu-id="2b764-263">?x=3</span><span class="sxs-lookup"><span data-stu-id="2b764-263">?x=3</span></span>  
  
- <span data-ttu-id="2b764-264">?x=1</span><span class="sxs-lookup"><span data-stu-id="2b764-264">?x=1</span></span>  
  
- <span data-ttu-id="2b764-265">?</span><span class="sxs-lookup"><span data-stu-id="2b764-265">?</span></span>  
  
- <span data-ttu-id="2b764-266">?</span><span class="sxs-lookup"><span data-stu-id="2b764-266">?</span></span> <span data-ttu-id="2b764-267">x={var}</span><span class="sxs-lookup"><span data-stu-id="2b764-267">x={var}</span></span>  
  
- <span data-ttu-id="2b764-268">?</span><span class="sxs-lookup"><span data-stu-id="2b764-268">?</span></span>  
  
- <span data-ttu-id="2b764-269">?m=get&c=rss</span><span class="sxs-lookup"><span data-stu-id="2b764-269">?m=get&c=rss</span></span>  
  
- <span data-ttu-id="2b764-270">?m=put&c=rss</span><span class="sxs-lookup"><span data-stu-id="2b764-270">?m=put&c=rss</span></span>  
  
- <span data-ttu-id="2b764-271">?m=get&c=atom</span><span class="sxs-lookup"><span data-stu-id="2b764-271">?m=get&c=atom</span></span>  
  
- <span data-ttu-id="2b764-272">?m=put&c=atom</span><span class="sxs-lookup"><span data-stu-id="2b764-272">?m=put&c=atom</span></span>  
  
 <span data-ttu-id="2b764-273">下列查詢字串範本組本身語意都很模糊：</span><span class="sxs-lookup"><span data-stu-id="2b764-273">The following sets of query string templates are ambiguous within themselves:</span></span>  
  
- <span data-ttu-id="2b764-274">?x=1</span><span class="sxs-lookup"><span data-stu-id="2b764-274">?x=1</span></span>  
  
- <span data-ttu-id="2b764-275">?x={var}</span><span class="sxs-lookup"><span data-stu-id="2b764-275">?x={var}</span></span>  
  
 <span data-ttu-id="2b764-276">"x=1"：與兩個範本相符。</span><span class="sxs-lookup"><span data-stu-id="2b764-276">"x=1" - Matches both templates.</span></span>  
  
- <span data-ttu-id="2b764-277">?x=1</span><span class="sxs-lookup"><span data-stu-id="2b764-277">?x=1</span></span>  
  
- <span data-ttu-id="2b764-278">?y=2</span><span class="sxs-lookup"><span data-stu-id="2b764-278">?y=2</span></span>  
  
 <span data-ttu-id="2b764-279">"x=1&y=2" 與兩個範本相符。</span><span class="sxs-lookup"><span data-stu-id="2b764-279">"x=1&y=2" matches both templates.</span></span> <span data-ttu-id="2b764-280">這是因為查詢字串所包含的查詢字串變數數量可能超出範本所符合的查詢字串變數數量。</span><span class="sxs-lookup"><span data-stu-id="2b764-280">This is because a query string may contain more query string variables then the template it matches.</span></span>  
  
- <span data-ttu-id="2b764-281">?x=1</span><span class="sxs-lookup"><span data-stu-id="2b764-281">?x=1</span></span>  
  
- <span data-ttu-id="2b764-282">?x=1&y={var}</span><span class="sxs-lookup"><span data-stu-id="2b764-282">?x=1&y={var}</span></span>  
  
 <span data-ttu-id="2b764-283">"x=1&y=3" 與兩個範本相符。</span><span class="sxs-lookup"><span data-stu-id="2b764-283">"x=1&y=3" matches both templates.</span></span>  
  
- <span data-ttu-id="2b764-284">?x=3&y=4</span><span class="sxs-lookup"><span data-stu-id="2b764-284">?x=3&y=4</span></span>  
  
- <span data-ttu-id="2b764-285">?x=3&z=5</span><span class="sxs-lookup"><span data-stu-id="2b764-285">?x=3&z=5</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b764-286">當字元 á 與 Á 出現在 URI 路徑或 <xref:System.UriTemplate> 路徑片段常值中時，兩者將被視為不同的字元 (但是字元 a 與 A 則被視為相同)。</span><span class="sxs-lookup"><span data-stu-id="2b764-286">The characters á and Á are considered to be different characters when they appear as part of a URI path or <xref:System.UriTemplate> path segment literal (but the characters a and A are considered to be the same).</span></span> <span data-ttu-id="2b764-287">當字元 á 與 Á 出現在 <xref:System.UriTemplate> {variableName} 或查詢字串中時，兩者將被視為相同的字元 (而且字元 a 與 A 亦將被視為相同)。</span><span class="sxs-lookup"><span data-stu-id="2b764-287">The characters á and Á are considered to be the same characters when they appear as part of a <xref:System.UriTemplate> {variableName} or a query string (and a and A are also considered to be the same characters).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b764-288">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b764-288">See Also</span></span>  
 [<span data-ttu-id="2b764-289">WCF Web HTTP 程式設計模型概觀</span><span class="sxs-lookup"><span data-stu-id="2b764-289">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 [<span data-ttu-id="2b764-290">WCF Web HTTP 程式設計物件模型</span><span class="sxs-lookup"><span data-stu-id="2b764-290">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 [<span data-ttu-id="2b764-291">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="2b764-291">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)  
 [<span data-ttu-id="2b764-292">UriTemplate 資料表</span><span class="sxs-lookup"><span data-stu-id="2b764-292">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [<span data-ttu-id="2b764-293">UriTemplate 資料表發送器</span><span class="sxs-lookup"><span data-stu-id="2b764-293">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
