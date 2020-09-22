---
title: My.WebServices 物件
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: 0b63b44c2cd9d55094fb83fed6c04e4de528a25c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867206"
---
# <a name="mywebservices-object"></a><span data-ttu-id="69784-102">My.WebServices 物件</span><span class="sxs-lookup"><span data-stu-id="69784-102">My.WebServices Object</span></span>

<span data-ttu-id="69784-103">提供屬性，用來建立及存取目前專案所參考之每個 XML Web Service 的單一實例。</span><span class="sxs-lookup"><span data-stu-id="69784-103">Provides properties for creating and accessing a single instance of each XML Web service referenced by the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69784-104">備註</span><span class="sxs-lookup"><span data-stu-id="69784-104">Remarks</span></span>  

 <span data-ttu-id="69784-105">`My.WebServices` 物件會提供目前專案所參考之每個 Web 服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="69784-105">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="69784-106">每個執行個體都是依需要具現化。</span><span class="sxs-lookup"><span data-stu-id="69784-106">Each instance is instantiated on demand.</span></span> <span data-ttu-id="69784-107">您可以透過 `My.WebServices` 物件的屬性來存取這些 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="69784-107">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="69784-108">屬性名稱和屬性存取的 Web 服務名稱相同。</span><span class="sxs-lookup"><span data-stu-id="69784-108">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="69784-109">任何繼承自 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> 的類別都是 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="69784-109">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span> <span data-ttu-id="69784-110">如需將 Web 服務加入至專案的詳細資訊，請參閱 [存取應用程式 Web 服務](../../developing-apps/programming/accessing-application-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="69784-110">For information about adding Web services to a project, see [Accessing Application Web Services](../../developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="69784-111">`My.WebServices`物件只會公開與目前專案相關聯的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="69784-111">The `My.WebServices` object exposes only the Web services associated with the current project.</span></span> <span data-ttu-id="69784-112">它不會提供參考 Dll 中宣告之 Web 服務的存取權。</span><span class="sxs-lookup"><span data-stu-id="69784-112">It does not provide access to Web services declared in referenced DLLs.</span></span> <span data-ttu-id="69784-113">若要存取 DLL 提供的 Web 服務，您必須使用 *DllName*格式的 web 服務的限定名稱。*WebServiceName*。</span><span class="sxs-lookup"><span data-stu-id="69784-113">To access a Web service that a DLL provides, you must use the qualified name of the Web service, in the form *DllName*.*WebServiceName*.</span></span> <span data-ttu-id="69784-114">如需詳細資訊，請參閱 [存取應用程式 Web 服務](../../developing-apps/programming/accessing-application-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="69784-114">For more information, see [Accessing Application Web Services](../../developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="69784-115">Web 應用程式無法使用物件和其屬性。</span><span class="sxs-lookup"><span data-stu-id="69784-115">The object and its properties are not available for Web applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="69784-116">屬性</span><span class="sxs-lookup"><span data-stu-id="69784-116">Properties</span></span>  

 <span data-ttu-id="69784-117">物件的每個屬性都 `My.WebServices` 可讓您存取目前專案所參考的 Web 服務實例。</span><span class="sxs-lookup"><span data-stu-id="69784-117">Each property of the `My.WebServices` object provides access to an instance of a Web service referenced by the current project.</span></span> <span data-ttu-id="69784-118">屬性的名稱與屬性所存取的 Web 服務名稱相同，而且屬性型別與 Web 服務的型別相同。</span><span class="sxs-lookup"><span data-stu-id="69784-118">The name of the property is the same as the name of the Web service that the property accesses, and the property type is the same as the Web service's type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69784-119">如果發生名稱衝突，用於存取 Web 服務的屬性名稱是*RootNamespace*_*命名空間* \_ *ServiceName*。</span><span class="sxs-lookup"><span data-stu-id="69784-119">If there is a name collision, the property name for accessing a Web service is *RootNamespace*_*Namespace*\_*ServiceName*.</span></span> <span data-ttu-id="69784-120">例如，請考慮兩個名為的 Web 服務 `Service1` 。</span><span class="sxs-lookup"><span data-stu-id="69784-120">For example, consider two Web services named `Service1`.</span></span> <span data-ttu-id="69784-121">如果其中一項服務是在根命名空間中， `WindowsApplication1` 而在命名空間中 `Namespace1` ，您就可以使用來存取該服務 `My.WebServices.WindowsApplication1_Namespace1_Service1` 。</span><span class="sxs-lookup"><span data-stu-id="69784-121">If one of these services is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that service by using `My.WebServices.WindowsApplication1_Namespace1_Service1`.</span></span>  
  
 <span data-ttu-id="69784-122">當您第一次存取物件的其中一個 `My.WebServices` 屬性時，它會建立新的 Web 服務實例，並加以儲存。</span><span class="sxs-lookup"><span data-stu-id="69784-122">When you first access one of the `My.WebServices` object's properties, it creates a new instance of the Web service and stores it.</span></span> <span data-ttu-id="69784-123">該屬性的後續存取會傳回該 Web 服務的實例。</span><span class="sxs-lookup"><span data-stu-id="69784-123">Subsequent accesses of that property return that instance of the Web service.</span></span>  
  
 <span data-ttu-id="69784-124">您可以藉由指派 `Nothing` 給該 web 服務的屬性來處置 web 服務。</span><span class="sxs-lookup"><span data-stu-id="69784-124">You can dispose of a Web service by assigning `Nothing` to the property for that Web service.</span></span> <span data-ttu-id="69784-125">屬性 setter 會指派 `Nothing` 給儲存的值。</span><span class="sxs-lookup"><span data-stu-id="69784-125">The property setter assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="69784-126">如果您將以外的任何值指派 `Nothing` 給屬性，setter 會擲回 <xref:System.ArgumentException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="69784-126">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="69784-127">您可以 `My.WebServices` 使用 or 運算子測試物件的屬性是否儲存 Web 服務的實例 `Is` `IsNot` 。</span><span class="sxs-lookup"><span data-stu-id="69784-127">You can test whether a property of the `My.WebServices` object stores an instance of the Web service by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="69784-128">您可以使用這些運算子來檢查屬性的值是否為 `Nothing` 。</span><span class="sxs-lookup"><span data-stu-id="69784-128">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69784-129">一般而言， `Is` or `IsNot` 運算子必須讀取屬性的值才能執行比較。</span><span class="sxs-lookup"><span data-stu-id="69784-129">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="69784-130">但是，如果屬性目前儲存 `Nothing` ，則屬性會建立 Web 服務的新實例，然後傳回該實例。</span><span class="sxs-lookup"><span data-stu-id="69784-130">However, if the property currently stores `Nothing`, the property creates a new instance of the Web service and then returns that instance.</span></span> <span data-ttu-id="69784-131">不過，Visual Basic 編譯器會特別處理物件的屬性 `My.WebServices` ，並允許 `Is` 或 `IsNot` 運算子檢查屬性的狀態，而不會變更其值。</span><span class="sxs-lookup"><span data-stu-id="69784-131">However, the Visual Basic compiler treats the properties of the `My.WebServices` object specially, and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69784-132">範例</span><span class="sxs-lookup"><span data-stu-id="69784-132">Example</span></span>  

 <span data-ttu-id="69784-133">此範例會呼叫 `FahrenheitToCelsius` `TemperatureConverter` XML Web Service 的方法，並傳回結果。</span><span class="sxs-lookup"><span data-stu-id="69784-133">This example calls the `FahrenheitToCelsius` method of the `TemperatureConverter` XML Web service, and returns the result.</span></span>  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 <span data-ttu-id="69784-134">若要讓此範例能夠運作，您的專案必須參考名為的 Web 服務 `Converter` ，而該 web 服務必須公開 `ConvertTemperature` 方法。</span><span class="sxs-lookup"><span data-stu-id="69784-134">For this example to work, your project must reference a Web service named `Converter`, and that Web service must expose the `ConvertTemperature` method.</span></span> <span data-ttu-id="69784-135">如需詳細資訊，請參閱 [存取應用程式 Web 服務](../../developing-apps/programming/accessing-application-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="69784-135">For more information, see [Accessing Application Web Services](../../developing-apps/programming/accessing-application-web-services.md).</span></span>  
  
 <span data-ttu-id="69784-136">這段程式碼無法在 Web 應用程式專案中運作。</span><span class="sxs-lookup"><span data-stu-id="69784-136">This code does not work in a Web application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69784-137">規格需求</span><span class="sxs-lookup"><span data-stu-id="69784-137">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="69784-138">可用性（依專案類型）</span><span class="sxs-lookup"><span data-stu-id="69784-138">Availability by Project Type</span></span>  
  
|<span data-ttu-id="69784-139">專案類型</span><span class="sxs-lookup"><span data-stu-id="69784-139">Project type</span></span>|<span data-ttu-id="69784-140">可用</span><span class="sxs-lookup"><span data-stu-id="69784-140">Available</span></span>|  
|---|---|  
|<span data-ttu-id="69784-141">Windows 應用程式</span><span class="sxs-lookup"><span data-stu-id="69784-141">Windows Application</span></span>|<span data-ttu-id="69784-142">**是**</span><span class="sxs-lookup"><span data-stu-id="69784-142">**Yes**</span></span>|  
|<span data-ttu-id="69784-143">類別庫</span><span class="sxs-lookup"><span data-stu-id="69784-143">Class Library</span></span>|<span data-ttu-id="69784-144">**是**</span><span class="sxs-lookup"><span data-stu-id="69784-144">**Yes**</span></span>|  
|<span data-ttu-id="69784-145">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="69784-145">Console Application</span></span>|<span data-ttu-id="69784-146">**是**</span><span class="sxs-lookup"><span data-stu-id="69784-146">**Yes**</span></span>|  
|<span data-ttu-id="69784-147">Windows 控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="69784-147">Windows Control Library</span></span>|<span data-ttu-id="69784-148">**是**</span><span class="sxs-lookup"><span data-stu-id="69784-148">**Yes**</span></span>|  
|<span data-ttu-id="69784-149">Web 控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="69784-149">Web Control Library</span></span>|<span data-ttu-id="69784-150">**是**</span><span class="sxs-lookup"><span data-stu-id="69784-150">**Yes**</span></span>|  
|<span data-ttu-id="69784-151">Windows 服務</span><span class="sxs-lookup"><span data-stu-id="69784-151">Windows Service</span></span>|<span data-ttu-id="69784-152">**是**</span><span class="sxs-lookup"><span data-stu-id="69784-152">**Yes**</span></span>|  
|<span data-ttu-id="69784-153">網站</span><span class="sxs-lookup"><span data-stu-id="69784-153">Web Site</span></span>|<span data-ttu-id="69784-154">否</span><span class="sxs-lookup"><span data-stu-id="69784-154">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="69784-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69784-155">See also</span></span>

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [<span data-ttu-id="69784-156">存取應用程式 Web 服務</span><span class="sxs-lookup"><span data-stu-id="69784-156">Accessing Application Web Services</span></span>](../../developing-apps/programming/accessing-application-web-services.md)
