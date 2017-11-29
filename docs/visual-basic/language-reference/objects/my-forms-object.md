---
title: "My.Forms 物件"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords: My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a5aa7af1f07a29660335d968c1ecc17be5f8beec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="myforms-object"></a><span data-ttu-id="4576d-102">My.Forms 物件</span><span class="sxs-lookup"><span data-stu-id="4576d-102">My.Forms Object</span></span>
<span data-ttu-id="4576d-103">提供存取目前的專案中所宣告的每個 Windows form 的執行個體的屬性。</span><span class="sxs-lookup"><span data-stu-id="4576d-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4576d-104">備註</span><span class="sxs-lookup"><span data-stu-id="4576d-104">Remarks</span></span>  
 <span data-ttu-id="4576d-105">`My.Forms`物件提供每個表單目前專案中的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4576d-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="4576d-106">屬性的名稱是表單的屬性存取的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="4576d-106">The name of the property is the same as the name of the form that the property accesses.</span></span> <span data-ttu-id="4576d-107">將表單加入專案的相關資訊，請參閱[How to： 將 Windows Form 加入至專案](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1)。</span><span class="sxs-lookup"><span data-stu-id="4576d-107">For information about adding forms to a project, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
 <span data-ttu-id="4576d-108">您可以存取所提供的表單`My.Forms`使用的表單，而不加限定的名稱。</span><span class="sxs-lookup"><span data-stu-id="4576d-108">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="4576d-109">因為屬性名稱做為表單的類型名稱相同，這可讓您存取表單，如同它已有預設的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4576d-109">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="4576d-110">例如，`My.Forms.Form1.Show` 等於 `Form1.Show`。</span><span class="sxs-lookup"><span data-stu-id="4576d-110">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>  
  
 <span data-ttu-id="4576d-111">`My.Forms`物件會公開只與目前的專案相關聯的表單。</span><span class="sxs-lookup"><span data-stu-id="4576d-111">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="4576d-112">它不提供宣告中被參考 Dll 的表單的存取權。</span><span class="sxs-lookup"><span data-stu-id="4576d-112">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="4576d-113">若要存取的 DLL 所提供的表單，您必須使用限定的名稱的格式，撰寫為*DllName*。*FormName*。</span><span class="sxs-lookup"><span data-stu-id="4576d-113">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>  
  
 <span data-ttu-id="4576d-114">您可以使用<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>屬性來取得集合中的應用程式的所有開啟表單。</span><span class="sxs-lookup"><span data-stu-id="4576d-114">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>  
  
 <span data-ttu-id="4576d-115">物件和其屬性的僅適用於 Windows 應用程式。</span><span class="sxs-lookup"><span data-stu-id="4576d-115">The object and its properties are available only for Windows applications.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4576d-116">屬性</span><span class="sxs-lookup"><span data-stu-id="4576d-116">Properties</span></span>  
 <span data-ttu-id="4576d-117">每一個屬性的`My.Forms`物件提供存取目前的專案中的表單之執行個體。</span><span class="sxs-lookup"><span data-stu-id="4576d-117">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="4576d-118">屬性的名稱與相同的屬性存取，表單的名稱，屬性類型就是表單的類型相同。</span><span class="sxs-lookup"><span data-stu-id="4576d-118">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4576d-119">如果沒有名稱衝突，存取表單的屬性名稱是*RootNamespace*_*命名空間*\_*FormName*。</span><span class="sxs-lookup"><span data-stu-id="4576d-119">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="4576d-120">例如，假設名為兩種形式`Form1.`其中一個表單是否在根命名空間`WindowsApplication1`和命名空間`Namespace1`，存取透過該表單`My.Forms.WindowsApplication1_Namespace1_Form1`。</span><span class="sxs-lookup"><span data-stu-id="4576d-120">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>  
  
 <span data-ttu-id="4576d-121">`My.Forms`物件提供存取的應用程式的主要表單，以在啟動時建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="4576d-121">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="4576d-122">對於所有其他的表單，`My.Forms`時它存取，並將其物件會建立表單的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="4576d-122">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="4576d-123">後續嘗試存取該屬性會傳回該執行個體的表單。</span><span class="sxs-lookup"><span data-stu-id="4576d-123">Subsequent attempts to access that property return that instance of the form.</span></span>  
  
 <span data-ttu-id="4576d-124">您可以藉由指派處置表單`Nothing`設為該表單的屬性。</span><span class="sxs-lookup"><span data-stu-id="4576d-124">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="4576d-125">屬性 setter 呼叫<xref:System.Windows.Forms.Form.Close%2A>方法的表單，然後指派`Nothing`儲存值。</span><span class="sxs-lookup"><span data-stu-id="4576d-125">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="4576d-126">如果您指派以外的任何值`Nothing`於屬性 setter 會擲回<xref:System.ArgumentException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4576d-126">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="4576d-127">您可以測試是否屬性`My.Forms`物件儲存表單的執行個體使用`Is`或`IsNot`運算子。</span><span class="sxs-lookup"><span data-stu-id="4576d-127">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="4576d-128">您可以使用這些運算子來檢查屬性的值是否為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="4576d-128">You can use those operators to check if the value of the property is `Nothing`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4576d-129">一般而言，`Is`或`IsNot`運算子具有讀取要比較之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="4576d-129">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="4576d-130">不過，如果屬性目前儲存`Nothing`，屬性建立表單的新執行個體，然後傳回該執行個體。</span><span class="sxs-lookup"><span data-stu-id="4576d-130">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="4576d-131">不過，Visual Basic 編譯器會將屬性`My.Forms`物件以不同的方式，並可讓`Is`或`IsNot`運算子來檢查屬性狀態，而不會變更其值。</span><span class="sxs-lookup"><span data-stu-id="4576d-131">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4576d-132">範例</span><span class="sxs-lookup"><span data-stu-id="4576d-132">Example</span></span>  
 <span data-ttu-id="4576d-133">這個範例會變更預設的標題`SidebarMenu`表單。</span><span class="sxs-lookup"><span data-stu-id="4576d-133">This example changes the title of the default `SidebarMenu` form.</span></span>  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 <span data-ttu-id="4576d-134">要讓範例能夠運作，您的專案必須擁有名為表單`SidebarMenu`。</span><span class="sxs-lookup"><span data-stu-id="4576d-134">For this example to work, your project must have a form named `SidebarMenu`.</span></span> <span data-ttu-id="4576d-135">如需詳細資訊，請參閱[How to： 將 Windows Form 加入至專案](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1)。</span><span class="sxs-lookup"><span data-stu-id="4576d-135">For more information, see [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).</span></span>  
  
 <span data-ttu-id="4576d-136">這段程式碼只會在 Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="4576d-136">This code will work only in a Windows Application project.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4576d-137">需求</span><span class="sxs-lookup"><span data-stu-id="4576d-137">Requirements</span></span>  
  
### <a name="availability-by-project-type"></a><span data-ttu-id="4576d-138">專案類型的可用性</span><span class="sxs-lookup"><span data-stu-id="4576d-138">Availability by Project Type</span></span>  
  
|<span data-ttu-id="4576d-139">專案類型</span><span class="sxs-lookup"><span data-stu-id="4576d-139">Project type</span></span>|<span data-ttu-id="4576d-140">可用</span><span class="sxs-lookup"><span data-stu-id="4576d-140">Available</span></span>|  
|---|---|  
|<span data-ttu-id="4576d-141">Windows 應用程式</span><span class="sxs-lookup"><span data-stu-id="4576d-141">Windows Application</span></span>|<span data-ttu-id="4576d-142">**是**</span><span class="sxs-lookup"><span data-stu-id="4576d-142">**Yes**</span></span>|  
|<span data-ttu-id="4576d-143">類別庫</span><span class="sxs-lookup"><span data-stu-id="4576d-143">Class Library</span></span>|<span data-ttu-id="4576d-144">否</span><span class="sxs-lookup"><span data-stu-id="4576d-144">No</span></span>|  
|<span data-ttu-id="4576d-145">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="4576d-145">Console Application</span></span>|<span data-ttu-id="4576d-146">否</span><span class="sxs-lookup"><span data-stu-id="4576d-146">No</span></span>|  
|<span data-ttu-id="4576d-147">Windows 控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="4576d-147">Windows Control Library</span></span>|<span data-ttu-id="4576d-148">否</span><span class="sxs-lookup"><span data-stu-id="4576d-148">No</span></span>|  
|<span data-ttu-id="4576d-149">Web 控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="4576d-149">Web Control Library</span></span>|<span data-ttu-id="4576d-150">否</span><span class="sxs-lookup"><span data-stu-id="4576d-150">No</span></span>|  
|<span data-ttu-id="4576d-151">Windows 服務</span><span class="sxs-lookup"><span data-stu-id="4576d-151">Windows Service</span></span>|<span data-ttu-id="4576d-152">否</span><span class="sxs-lookup"><span data-stu-id="4576d-152">No</span></span>|  
|<span data-ttu-id="4576d-153">網站</span><span class="sxs-lookup"><span data-stu-id="4576d-153">Web Site</span></span>|<span data-ttu-id="4576d-154">否</span><span class="sxs-lookup"><span data-stu-id="4576d-154">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4576d-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4576d-155">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Form.Close%2A>  
 [<span data-ttu-id="4576d-156">物件</span><span class="sxs-lookup"><span data-stu-id="4576d-156">Objects</span></span>](../../../visual-basic/language-reference/objects/index.md)  
 [<span data-ttu-id="4576d-157">如何： 將 Windows Form 加入專案</span><span class="sxs-lookup"><span data-stu-id="4576d-157">How to: Add Windows Forms to a Project</span></span>](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1)  
 [<span data-ttu-id="4576d-158">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="4576d-158">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="4576d-159">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="4576d-159">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="4576d-160">存取應用程式表單</span><span class="sxs-lookup"><span data-stu-id="4576d-160">Accessing Application Forms</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
