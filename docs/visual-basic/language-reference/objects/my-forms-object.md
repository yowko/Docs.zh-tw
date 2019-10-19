---
title: Forms 物件（Visual Basic）
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 9a0b3b9202972122aea4a7147d8d872486418264
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581875"
---
# <a name="myforms-object"></a><span data-ttu-id="42323-102">My.Forms 物件</span><span class="sxs-lookup"><span data-stu-id="42323-102">My.Forms Object</span></span>

<span data-ttu-id="42323-103">提供屬性，以存取目前專案中宣告之每個 Windows form 的實例。</span><span class="sxs-lookup"><span data-stu-id="42323-103">Provides properties for accessing an instance of each Windows form declared in the current project.</span></span>

## <a name="remarks"></a><span data-ttu-id="42323-104">備註</span><span class="sxs-lookup"><span data-stu-id="42323-104">Remarks</span></span>

<span data-ttu-id="42323-105">@No__t_0 物件會在目前的專案中提供每個表單的實例。</span><span class="sxs-lookup"><span data-stu-id="42323-105">The `My.Forms` object provides an instance of each form in the current project.</span></span> <span data-ttu-id="42323-106">屬性的名稱與屬性所存取的表單名稱相同。</span><span class="sxs-lookup"><span data-stu-id="42323-106">The name of the property is the same as the name of the form that the property accesses.</span></span>

<span data-ttu-id="42323-107">您可以使用表單的名稱，而不需限定，來存取 `My.Forms` 物件所提供的表單。</span><span class="sxs-lookup"><span data-stu-id="42323-107">You can access the forms provided by the `My.Forms` object by using the name of the form, without qualification.</span></span> <span data-ttu-id="42323-108">因為屬性名稱與表單的類型名稱相同，所以可讓您存取表單，就像它有預設的實例一樣。</span><span class="sxs-lookup"><span data-stu-id="42323-108">Because the property name is the same as the form's type name, this allows you to access a form as if it had a default instance.</span></span> <span data-ttu-id="42323-109">例如，`My.Forms.Form1.Show` 等於 `Form1.Show`。</span><span class="sxs-lookup"><span data-stu-id="42323-109">For example, `My.Forms.Form1.Show` is equivalent to `Form1.Show`.</span></span>

<span data-ttu-id="42323-110">@No__t_0 物件只會公開與目前專案相關聯的表單。</span><span class="sxs-lookup"><span data-stu-id="42323-110">The `My.Forms` object exposes only the forms associated with the current project.</span></span> <span data-ttu-id="42323-111">它不會提供參考的 Dll 中所宣告之表單的存取權。</span><span class="sxs-lookup"><span data-stu-id="42323-111">It does not provide access to forms declared in referenced DLLs.</span></span> <span data-ttu-id="42323-112">若要存取 DLL 提供的表單，您必須使用表單的限定名稱，此格式寫成*DllName*。*FormName*。</span><span class="sxs-lookup"><span data-stu-id="42323-112">To access a form that a DLL provides, you must use the qualified name of the form, written as *DllName*.*FormName*.</span></span>

<span data-ttu-id="42323-113">您可以使用 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> 屬性來取得應用程式所有開啟表單的集合。</span><span class="sxs-lookup"><span data-stu-id="42323-113">You can use the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> property to get a collection of all the application's open forms.</span></span>

<span data-ttu-id="42323-114">物件及其屬性僅適用于 Windows 應用程式。</span><span class="sxs-lookup"><span data-stu-id="42323-114">The object and its properties are available only for Windows applications.</span></span>

## <a name="properties"></a><span data-ttu-id="42323-115">內容</span><span class="sxs-lookup"><span data-stu-id="42323-115">Properties</span></span>

<span data-ttu-id="42323-116">@No__t_0 物件的每個屬性都可讓您存取目前專案中的表單實例。</span><span class="sxs-lookup"><span data-stu-id="42323-116">Each property of the `My.Forms` object provides access to an instance of a form in the current project.</span></span> <span data-ttu-id="42323-117">屬性的名稱與屬性所存取的表單名稱相同，而且屬性類型與表單的類型相同。</span><span class="sxs-lookup"><span data-stu-id="42323-117">The name of the property is the same as the name of the form that the property accesses, and the property type is the same as the form's type.</span></span>

> [!NOTE]
> <span data-ttu-id="42323-118">如果發生名稱衝突，存取表單的屬性名稱是*RootNamespace*_*Namespace* \_*FormName*。</span><span class="sxs-lookup"><span data-stu-id="42323-118">If there is a name collision, the property name to access a form is *RootNamespace*_*Namespace*\_*FormName*.</span></span> <span data-ttu-id="42323-119">例如，假設有兩個名為的表單 `Form1.`If 其中一個表單位於根命名空間中 `WindowsApplication1` 而且在命名空間 `Namespace1` 中，您會透過 `My.Forms.WindowsApplication1_Namespace1_Form1` 來存取該表單。</span><span class="sxs-lookup"><span data-stu-id="42323-119">For example, consider two forms named `Form1.`If one of these forms is in the root namespace `WindowsApplication1` and in the namespace `Namespace1`, you would access that form through `My.Forms.WindowsApplication1_Namespace1_Form1`.</span></span>

<span data-ttu-id="42323-120">@No__t_0 物件提供在啟動時所建立之應用程式主要表單實例的存取權。</span><span class="sxs-lookup"><span data-stu-id="42323-120">The `My.Forms` object provides access to the instance of the application's main form that was created on startup.</span></span> <span data-ttu-id="42323-121">對於所有其他表單，`My.Forms` 物件會在存取並儲存表單時，建立其新的實例。</span><span class="sxs-lookup"><span data-stu-id="42323-121">For all other forms, the `My.Forms` object creates a new instance of the form when it is accessed and stores it.</span></span> <span data-ttu-id="42323-122">後續嘗試存取該屬性時，會傳回該表單的實例。</span><span class="sxs-lookup"><span data-stu-id="42323-122">Subsequent attempts to access that property return that instance of the form.</span></span>

<span data-ttu-id="42323-123">您可以藉由將 `Nothing` 指派給該表單的屬性來處置表單。</span><span class="sxs-lookup"><span data-stu-id="42323-123">You can dispose of a form by assigning `Nothing` to the property for that form.</span></span> <span data-ttu-id="42323-124">屬性 setter 會呼叫表單的 <xref:System.Windows.Forms.Form.Close%2A> 方法，然後將 `Nothing` 指派給儲存的值。</span><span class="sxs-lookup"><span data-stu-id="42323-124">The property setter calls the <xref:System.Windows.Forms.Form.Close%2A> method of the form, and then assigns `Nothing` to the stored value.</span></span> <span data-ttu-id="42323-125">如果您將 `Nothing` 以外的任何值指派給屬性，則 setter 會擲回 <xref:System.ArgumentException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="42323-125">If you assign any value other than `Nothing` to the property, the setter throws an <xref:System.ArgumentException> exception.</span></span>

<span data-ttu-id="42323-126">您可以使用 `Is` 或 `IsNot` 運算子，測試 `My.Forms` 物件的屬性是否儲存表單的實例。</span><span class="sxs-lookup"><span data-stu-id="42323-126">You can test whether a property of the `My.Forms` object stores an instance of the form by using the `Is` or `IsNot` operator.</span></span> <span data-ttu-id="42323-127">您可以使用這些運算子來檢查屬性的值是否為 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="42323-127">You can use those operators to check if the value of the property is `Nothing`.</span></span>

> [!NOTE]
> <span data-ttu-id="42323-128">一般來說，`Is` 或 `IsNot` 運算子必須讀取屬性的值，才能執行比較。</span><span class="sxs-lookup"><span data-stu-id="42323-128">Typically, the `Is` or `IsNot` operator has to read the value of the property to perform the comparison.</span></span> <span data-ttu-id="42323-129">不過，如果屬性目前儲存 `Nothing`，則屬性會建立表單的新實例，然後傳回該實例。</span><span class="sxs-lookup"><span data-stu-id="42323-129">However, if the property currently stores `Nothing`, the property creates a new instance of the form and then returns that instance.</span></span> <span data-ttu-id="42323-130">不過，Visual Basic 編譯器會以不同的方式來處理 `My.Forms` 物件的屬性，並允許 `Is` 或 `IsNot` 運算子檢查屬性的狀態，而不需要變更其值。</span><span class="sxs-lookup"><span data-stu-id="42323-130">However, the Visual Basic compiler treats the properties of the `My.Forms` object differently and allows the `Is` or `IsNot` operator to check the status of the property without altering its value.</span></span>

## <a name="example"></a><span data-ttu-id="42323-131">範例</span><span class="sxs-lookup"><span data-stu-id="42323-131">Example</span></span>

<span data-ttu-id="42323-132">這個範例會變更預設 `SidebarMenu` 表單的標題。</span><span class="sxs-lookup"><span data-stu-id="42323-132">This example changes the title of the default `SidebarMenu` form.</span></span>

[!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]

<span data-ttu-id="42323-133">若要讓此範例能夠正常執行，您的專案必須具有名為 `SidebarMenu` 的表單。</span><span class="sxs-lookup"><span data-stu-id="42323-133">For this example to work, your project must have a form named `SidebarMenu`.</span></span>

<span data-ttu-id="42323-134">這段程式碼只適用于 Windows 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="42323-134">This code will work only in a Windows Application project.</span></span>

## <a name="requirements"></a><span data-ttu-id="42323-135">需求</span><span class="sxs-lookup"><span data-stu-id="42323-135">Requirements</span></span>

### <a name="availability-by-project-type"></a><span data-ttu-id="42323-136">依專案類型的可用性</span><span class="sxs-lookup"><span data-stu-id="42323-136">Availability by Project Type</span></span>

|<span data-ttu-id="42323-137">專案類型</span><span class="sxs-lookup"><span data-stu-id="42323-137">Project type</span></span>|<span data-ttu-id="42323-138">可用</span><span class="sxs-lookup"><span data-stu-id="42323-138">Available</span></span>|
|---|---|
|<span data-ttu-id="42323-139">Windows 應用程式</span><span class="sxs-lookup"><span data-stu-id="42323-139">Windows Application</span></span>|<span data-ttu-id="42323-140">**是**</span><span class="sxs-lookup"><span data-stu-id="42323-140">**Yes**</span></span>|
|<span data-ttu-id="42323-141">類別庫</span><span class="sxs-lookup"><span data-stu-id="42323-141">Class Library</span></span>|<span data-ttu-id="42323-142">否</span><span class="sxs-lookup"><span data-stu-id="42323-142">No</span></span>|
|<span data-ttu-id="42323-143">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="42323-143">Console Application</span></span>|<span data-ttu-id="42323-144">否</span><span class="sxs-lookup"><span data-stu-id="42323-144">No</span></span>|
|<span data-ttu-id="42323-145">Windows 控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="42323-145">Windows Control Library</span></span>|<span data-ttu-id="42323-146">否</span><span class="sxs-lookup"><span data-stu-id="42323-146">No</span></span>|
|<span data-ttu-id="42323-147">Web 控制項程式庫</span><span class="sxs-lookup"><span data-stu-id="42323-147">Web Control Library</span></span>|<span data-ttu-id="42323-148">否</span><span class="sxs-lookup"><span data-stu-id="42323-148">No</span></span>|
|<span data-ttu-id="42323-149">Windows 服務</span><span class="sxs-lookup"><span data-stu-id="42323-149">Windows Service</span></span>|<span data-ttu-id="42323-150">否</span><span class="sxs-lookup"><span data-stu-id="42323-150">No</span></span>|
|<span data-ttu-id="42323-151">網站</span><span class="sxs-lookup"><span data-stu-id="42323-151">Web Site</span></span>|<span data-ttu-id="42323-152">否</span><span class="sxs-lookup"><span data-stu-id="42323-152">No</span></span>|

## <a name="see-also"></a><span data-ttu-id="42323-153">請參閱</span><span class="sxs-lookup"><span data-stu-id="42323-153">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [<span data-ttu-id="42323-154">物件</span><span class="sxs-lookup"><span data-stu-id="42323-154">Objects</span></span>](../../../visual-basic/language-reference/objects/index.md)
- [<span data-ttu-id="42323-155">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="42323-155">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="42323-156">IsNot 運算子</span><span class="sxs-lookup"><span data-stu-id="42323-156">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="42323-157">存取應用程式表單</span><span class="sxs-lookup"><span data-stu-id="42323-157">Accessing Application Forms</span></span>](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
