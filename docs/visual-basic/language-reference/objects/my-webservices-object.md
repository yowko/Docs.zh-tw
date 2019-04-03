---
title: My.WebServices 物件 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: a60f32c4f581e42f240fca55ce496776c5511ba3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840428"
---
# <a name="mywebservices-object"></a><span data-ttu-id="c9f91-102">My.WebServices 物件</span><span class="sxs-lookup"><span data-stu-id="c9f91-102">My.WebServices Object</span></span>
<span data-ttu-id="c9f91-103">提供建立及存取目前專案所參考的每個 XML Web 服務的單一執行個體的屬性。</span><span class="sxs-lookup"><span data-stu-id="c9f91-103">Provides properties for creating and accessing a single instance of each XML Web service referenced by the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9f91-104">備註</span><span class="sxs-lookup"><span data-stu-id="c9f91-104">Remarks</span></span>  
 <span data-ttu-id="c9f91-105">`My.WebServices` 物件會提供目前專案所參考之每個 Web 服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c9f91-105">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="c9f91-106">每個執行個體都是依需要具現化。</span><span class="sxs-lookup"><span data-stu-id="c9f91-106">Each instance is instantiated on demand.</span></span> <span data-ttu-id="c9f91-107">您可以透過 `My.WebServices` 物件的屬性來存取這些 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="c9f91-107">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="c9f91-108">屬性名稱和屬性存取的 Web 服務名稱相同。</span><span class="sxs-lookup"><span data-stu-id="c9f91-108">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="c9f91-109">任何繼承自 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> 的類別都是 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="c9f91-109">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span> <span data-ttu-id="c9f91-110">Web 服務新增至專案的相關資訊，請參閱[存取應用程式 Web 服務](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c9f91-110">For information about adding Web services to a project, see [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="c9f91-111">`My.WebServices`物件會公開僅與目前專案相關聯的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="c9f91-111">The `My.WebServices` object exposes only the Web services associated with the current project.</span></span> <span data-ttu-id="c9f91-112">它不提供宣告參考的 Dll 中的 Web 服務的存取權。</span><span class="sxs-lookup"><span data-stu-id="c9f91-112">It does not provide access to Web services declared in referenced DLLs.</span></span> <span data-ttu-id="c9f91-113">若要存取 DLL 所提供的 Web 服務，您必須使用 Web 服務的限定的名稱，形式*DllName*。*WebServiceName*。</span><span class="sxs-lookup"><span data-stu-id="c9f91-113">To access a Web service that a DLL provides, you must use the qualified name of the Web service, in the form *DllName*.*WebServiceName*.</span></span> <span data-ttu-id="c9f91-114">如需詳細資訊，請參閱 <<c0> [ 存取應用程式 Web 服務](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c9f91-114">For more information, see [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="c9f91-115">物件和其屬性不適用於 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c9f91-115">The object and its properties are not available for Web applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c9f91-116">屬性</span><span class="sxs-lookup"><span data-stu-id="c9f91-116">Properties</span></span>  
 <span data-ttu-id="c9f91-117">每一個屬性的`My.WebServices`物件提供存取目前專案所參考的 Web 服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c9f91-117">Each property of the `My.WebServices` object provides access to an instance of a Web service referenced by the current project.</span></span> <span data-ttu-id="c9f91-118">屬性的名稱與相同的屬性存取，Web 服務的名稱，屬性類型是與 Web 服務的型別相同。</span><span class="sxs-lookup"><span data-stu-id="c9f91-118">The name of the property is the same as the name of the Web service that the property accesses, and the property type is the same as the Web service's type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9f91-119">如果沒有名稱衝突，存取 Web 服務的屬性名稱是*RootNamespace*_*命名空間*\_*ServiceName*。</span><span class="sxs-lookup"><span data-stu-id="c9f91-119">If there is a name collision, the property name for accessing a Web service is *RootNamespace*_*Namespace*\_*ServiceName*.</span></span> <span data-ttu-id="c9f91-120">例如，假設名為兩個 Web 服務`Service1`。</span><span class="sxs-lookup"><span data-stu-id="c9f91-120">For example, consider two Web services named `Service1`.</span></span> <span data-ttu-id="c9f91-121">如果上述其中一個服務是在根命名空間`WindowsApplication1`和命名空間`Namespace1`，您會使用來存取該服務`My.WebServices.WindowsApplication1_Namespace1_Service1`。</span><span class="sxs-lookup"><span data-stu-id="c9f91-121">If one of these services is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that service by using `My.WebServices.WindowsApplication1_Namespace1_Service1`.</span></span>  
  
 <span data-ttu-id="c9f91-122">當您第一次存取其中一個`My.WebServices`物件的屬性，它會建立 Web 服務的新執行個體，並將它儲存。</span><span class="sxs-lookup"><span data-stu-id="c9f91-122">When you first access one of the `My.WebServices` object's properties, it creates a new instance of the Web service and stores it.</span></span> <span data-ttu-id="c9f91-123">後續的存取，該屬性會傳回該執行個體的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="c9f91-123">Subsequent accesses of that property return that instance of the Web service.</span></span>  
  
 <span data-ttu-id="c9f91-124">您可以藉由指定 Web 服務的處置`Nothing`設為該 Web 服務的屬性。</span><span class="sxs-lookup"><span data-stu-id="c9f91-124">You can dispose of a Web service by assigning `Nothing` to the property for that Web service.</span></span> <span data-ttu-id="c9f91-125">屬性 setter 指派`Nothing`的預存值。</span><span class="sxs-lookup"><span data-stu-id="c9f91-125">The property setter assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="c9f91-126">如果您指派任何值以外`Nothing`於屬性 setter 會擲回<xref:System.ArgumentException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c9f91-126">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="c9f91-127">您可以測試的屬性是否`My.WebServices`物件會儲存使用的 Web 服務的執行個體`Is`或`IsNot`運算子。</span><span class="sxs-lookup"><span data-stu-id="c9f91-127">You can test whether a property of the `My.WebServices` object stores an instance of the Web service by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="c9f91-128">您可以使用這些運算子，來檢查屬性的值是否為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="c9f91-128">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9f91-129">通常`Is`或`IsNot`操作員必須讀取要比較之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="c9f91-129">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="c9f91-130">不過，如果屬性目前儲存`Nothing`，屬性會建立 Web 服務的新執行個體，並接著會傳回該執行個體。</span><span class="sxs-lookup"><span data-stu-id="c9f91-130">However, if the property currently stores `Nothing`, the property creates a new instance of the Web service and then returns that instance.</span></span> <span data-ttu-id="c9f91-131">不過，Visual Basic 編譯器會將屬性`My.WebServices`物件，並允許`Is`或`IsNot`運算子來檢查屬性的狀態，而不需要變更其值。</span><span class="sxs-lookup"><span data-stu-id="c9f91-131">However, the Visual Basic compiler treats the properties of the `My.WebServices` object specially, and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9f91-132">範例</span><span class="sxs-lookup"><span data-stu-id="c9f91-132">Example</span></span>  
 <span data-ttu-id="c9f91-133">這個範例會呼叫`FahrenheitToCelsius`方法的`TemperatureConverter`XML Web service，並傳回結果。</span><span class="sxs-lookup"><span data-stu-id="c9f91-133">This example calls the `FahrenheitToCelsius` method of the `TemperatureConverter` XML Web service, and returns the result.</span></span>  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 <span data-ttu-id="c9f91-134">針對此範例正常運作，您的專案必須參考名為 Web 服務`Converter`，且該 Web 服務必須公開`ConvertTemperature`方法。</span><span class="sxs-lookup"><span data-stu-id="c9f91-134">For this example to work, your project must reference a Web service named `Converter`, and that Web service must expose the `ConvertTemperature` method.</span></span> <span data-ttu-id="c9f91-135">如需詳細資訊，請參閱 <<c0> [ 存取應用程式 Web 服務](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c9f91-135">For more information, see [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="c9f91-136">此程式碼無法運作的 Web 應用程式專案中。</span><span class="sxs-lookup"><span data-stu-id="c9f91-136">This code does not work in a Web application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9f91-137">需求</span><span class="sxs-lookup"><span data-stu-id="c9f91-137">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="c9f91-138">專案類型的可用性</span><span class="sxs-lookup"><span data-stu-id="c9f91-138">Availability by Project Type</span></span>  
  
|<span data-ttu-id="c9f91-139">專案類型</span><span class="sxs-lookup"><span data-stu-id="c9f91-139">Project type</span></span>|<span data-ttu-id="c9f91-140">可用</span><span class="sxs-lookup"><span data-stu-id="c9f91-140">Available</span></span>|  
|---|---|  
|<span data-ttu-id="c9f91-141">Windows 應用程式</span><span class="sxs-lookup"><span data-stu-id="c9f91-141">Windows Application</span></span>|<span data-ttu-id="c9f91-142">**是**</span><span class="sxs-lookup"><span data-stu-id="c9f91-142">**Yes**</span></span>|  
|<span data-ttu-id="c9f91-143">類別庫</span><span class="sxs-lookup"><span data-stu-id="c9f91-143">Class Library</span></span>|<span data-ttu-id="c9f91-144">**是**</span><span class="sxs-lookup"><span data-stu-id="c9f91-144">**Yes**</span></span>|  
|<span data-ttu-id="c9f91-145">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="c9f91-145">Console Application</span></span>|<span data-ttu-id="c9f91-146">**是**</span><span class="sxs-lookup"><span data-stu-id="c9f91-146">**Yes**</span></span>|  
|<span data-ttu-id="c9f91-147">Windows 控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="c9f91-147">Windows Control Library</span></span>|<span data-ttu-id="c9f91-148">**是**</span><span class="sxs-lookup"><span data-stu-id="c9f91-148">**Yes**</span></span>|  
|<span data-ttu-id="c9f91-149">Web 控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="c9f91-149">Web Control Library</span></span>|<span data-ttu-id="c9f91-150">**是**</span><span class="sxs-lookup"><span data-stu-id="c9f91-150">**Yes**</span></span>|  
|<span data-ttu-id="c9f91-151">Windows 服務</span><span class="sxs-lookup"><span data-stu-id="c9f91-151">Windows Service</span></span>|<span data-ttu-id="c9f91-152">**是**</span><span class="sxs-lookup"><span data-stu-id="c9f91-152">**Yes**</span></span>|  
|<span data-ttu-id="c9f91-153">網站</span><span class="sxs-lookup"><span data-stu-id="c9f91-153">Web Site</span></span>|<span data-ttu-id="c9f91-154">否</span><span class="sxs-lookup"><span data-stu-id="c9f91-154">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c9f91-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9f91-155">See also</span></span>

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [<span data-ttu-id="c9f91-156">存取應用程式 Web 服務</span><span class="sxs-lookup"><span data-stu-id="c9f91-156">Accessing Application Web Services</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
