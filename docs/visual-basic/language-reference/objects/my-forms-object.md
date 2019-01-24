---
title: My.Forms 物件 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 17042f60eb27c41640ef5d8c927c7acc5bc73183
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712614"
---
# <a name="myforms-object"></a><span data-ttu-id="1bb88-102">My.Forms 物件</span><span class="sxs-lookup"><span data-stu-id="1bb88-102">My.Forms Object</span></span>
<span data-ttu-id="1bb88-103">提供存取目前專案中宣告的每個 Windows form 的執行個體的屬性。</span><span class="sxs-lookup"><span data-stu-id="1bb88-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bb88-104">備註</span><span class="sxs-lookup"><span data-stu-id="1bb88-104">Remarks</span></span>  
 <span data-ttu-id="1bb88-105">`My.Forms`物件會提供目前專案中的每個表單的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1bb88-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="1bb88-106">屬性存取表單的名稱相同的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="1bb88-106">The name of the property is the same as the name of the form that the property accesses.</span></span>   
  
 <span data-ttu-id="1bb88-107">您可以存取所提供的表單`My.Forms`物件使用的格式，但是不限定的名稱。</span><span class="sxs-lookup"><span data-stu-id="1bb88-107">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="1bb88-108">屬性名稱是表單的類型名稱相同，因為這可讓您存取表單，如同它已有的預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="1bb88-108">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="1bb88-109">例如，`My.Forms.Form1.Show` 等於 `Form1.Show`。</span><span class="sxs-lookup"><span data-stu-id="1bb88-109">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>  
  
 <span data-ttu-id="1bb88-110">`My.Forms`物件會公開僅將目前的專案相關聯的表單。</span><span class="sxs-lookup"><span data-stu-id="1bb88-110">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="1bb88-111">它不提供宣告之參考的 Dll 中表單的存取。</span><span class="sxs-lookup"><span data-stu-id="1bb88-111">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="1bb88-112">若要存取 DLL 所提供的表單，您必須使用表單時，寫成的限定的名稱*DllName*。*FormName*。</span><span class="sxs-lookup"><span data-stu-id="1bb88-112">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>  
  
 <span data-ttu-id="1bb88-113">您可以使用<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>屬性來取得應用程式的所有開啟表單的集合。</span><span class="sxs-lookup"><span data-stu-id="1bb88-113">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>  
  
 <span data-ttu-id="1bb88-114">物件和其屬性是僅適用於 Windows 應用程式。</span><span class="sxs-lookup"><span data-stu-id="1bb88-114">The object and its properties are available only for Windows applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1bb88-115">屬性</span><span class="sxs-lookup"><span data-stu-id="1bb88-115">Properties</span></span>  
 <span data-ttu-id="1bb88-116">每一個屬性的`My.Forms`物件提供存取目前專案中撰寫表單的執行個體。</span><span class="sxs-lookup"><span data-stu-id="1bb88-116">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="1bb88-117">屬性的名稱與相同的屬性存取時，表單的名稱，屬性型別是表單的類型相同。</span><span class="sxs-lookup"><span data-stu-id="1bb88-117">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bb88-118">如果名稱有衝突時，要存取表單的屬性名稱是*RootNamespace*_*命名空間*\_*FormName*。</span><span class="sxs-lookup"><span data-stu-id="1bb88-118">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="1bb88-119">例如，假設名為兩種形式`Form1.`其中一種形式是否在根命名空間`WindowsApplication1`和命名空間`Namespace1`，存取透過該表單`My.Forms.WindowsApplication1_Namespace1_Form1`。</span><span class="sxs-lookup"><span data-stu-id="1bb88-119">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>  
  
 <span data-ttu-id="1bb88-120">`My.Forms`物件提供在啟動時建立的應用程式的主要表單的執行個體的存取。</span><span class="sxs-lookup"><span data-stu-id="1bb88-120">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="1bb88-121">所有其他形式，`My.Forms`物件會建立表單的新執行個體，當它存取，並將它儲存。</span><span class="sxs-lookup"><span data-stu-id="1bb88-121">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="1bb88-122">後續嘗試存取該屬性會傳回該執行個體的格式。</span><span class="sxs-lookup"><span data-stu-id="1bb88-122">Subsequent attempts to access that property return that instance of the form.</span></span>  
  
 <span data-ttu-id="1bb88-123">您可以藉由指派處置表單`Nothing`設為該表單的屬性。</span><span class="sxs-lookup"><span data-stu-id="1bb88-123">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="1bb88-124">屬性 setter 呼叫<xref:System.Windows.Forms.Form.Close%2A>方法的表單，然後指派`Nothing`的預存值。</span><span class="sxs-lookup"><span data-stu-id="1bb88-124">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="1bb88-125">如果您指派任何值以外`Nothing`於屬性 setter 會擲回<xref:System.ArgumentException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1bb88-125">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="1bb88-126">您可以測試的屬性是否`My.Forms`物件會儲存表單的執行個體使用`Is`或`IsNot`運算子。</span><span class="sxs-lookup"><span data-stu-id="1bb88-126">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="1bb88-127">您可以使用這些運算子，來檢查屬性的值是否為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="1bb88-127">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bb88-128">通常`Is`或`IsNot`操作員必須讀取要比較之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="1bb88-128">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="1bb88-129">不過，如果屬性目前儲存`Nothing`，屬性會建立表單的新執行個體，並接著會傳回該執行個體。</span><span class="sxs-lookup"><span data-stu-id="1bb88-129">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="1bb88-130">不過，Visual Basic 編譯器會將屬性`My.Forms`物件以不同的方式，並可讓`Is`或`IsNot`運算子來檢查屬性的狀態，而不需要變更其值。</span><span class="sxs-lookup"><span data-stu-id="1bb88-130">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bb88-131">範例</span><span class="sxs-lookup"><span data-stu-id="1bb88-131">Example</span></span>  
 <span data-ttu-id="1bb88-132">這個範例會變更的預設標題`SidebarMenu`表單。</span><span class="sxs-lookup"><span data-stu-id="1bb88-132">This example changes the title of the default `SidebarMenu` form.</span></span>  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 <span data-ttu-id="1bb88-133">此範例正常運作，您的專案必須表單名為`SidebarMenu`。</span><span class="sxs-lookup"><span data-stu-id="1bb88-133">For this example to work, your project must have a form named `SidebarMenu`.</span></span>  
  
 <span data-ttu-id="1bb88-134">此程式碼將僅適用於的 Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="1bb88-134">This code will work only in a Windows Application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bb88-135">需求</span><span class="sxs-lookup"><span data-stu-id="1bb88-135">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="1bb88-136">專案類型的可用性</span><span class="sxs-lookup"><span data-stu-id="1bb88-136">Availability by Project Type</span></span>  
  
|<span data-ttu-id="1bb88-137">專案類型</span><span class="sxs-lookup"><span data-stu-id="1bb88-137">Project type</span></span>|<span data-ttu-id="1bb88-138">可用</span><span class="sxs-lookup"><span data-stu-id="1bb88-138">Available</span></span>|  
|---|---|  
|<span data-ttu-id="1bb88-139">Windows 應用程式</span><span class="sxs-lookup"><span data-stu-id="1bb88-139">Windows Application</span></span>|<span data-ttu-id="1bb88-140">**是**</span><span class="sxs-lookup"><span data-stu-id="1bb88-140">**Yes**</span></span>|  
|<span data-ttu-id="1bb88-141">類別庫</span><span class="sxs-lookup"><span data-stu-id="1bb88-141">Class Library</span></span>|<span data-ttu-id="1bb88-142">否</span><span class="sxs-lookup"><span data-stu-id="1bb88-142">No</span></span>|  
|<span data-ttu-id="1bb88-143">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="1bb88-143">Console Application</span></span>|<span data-ttu-id="1bb88-144">否</span><span class="sxs-lookup"><span data-stu-id="1bb88-144">No</span></span>|  
|<span data-ttu-id="1bb88-145">Windows 控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="1bb88-145">Windows Control Library</span></span>|<span data-ttu-id="1bb88-146">否</span><span class="sxs-lookup"><span data-stu-id="1bb88-146">No</span></span>|  
|<span data-ttu-id="1bb88-147">Web 控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="1bb88-147">Web Control Library</span></span>|<span data-ttu-id="1bb88-148">否</span><span class="sxs-lookup"><span data-stu-id="1bb88-148">No</span></span>|  
|<span data-ttu-id="1bb88-149">Windows 服務</span><span class="sxs-lookup"><span data-stu-id="1bb88-149">Windows Service</span></span>|<span data-ttu-id="1bb88-150">否</span><span class="sxs-lookup"><span data-stu-id="1bb88-150">No</span></span>|  
|<span data-ttu-id="1bb88-151">網站</span><span class="sxs-lookup"><span data-stu-id="1bb88-151">Web Site</span></span>|<span data-ttu-id="1bb88-152">否</span><span class="sxs-lookup"><span data-stu-id="1bb88-152">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1bb88-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bb88-153">See also</span></span>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [<span data-ttu-id="1bb88-154">物件</span><span class="sxs-lookup"><span data-stu-id="1bb88-154">Objects</span></span>](../../../visual-basic/language-reference/objects/index.md)
- [<span data-ttu-id="1bb88-155">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="1bb88-155">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="1bb88-156">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="1bb88-156">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="1bb88-157">存取應用程式表單</span><span class="sxs-lookup"><span data-stu-id="1bb88-157">Accessing Application Forms</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
