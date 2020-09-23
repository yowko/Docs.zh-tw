---
title: References to Declared Elements
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: af5be47335b6d48bd6c0bccc30b8db15c9912807
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085876"
---
# <a name="references-to-declared-elements-visual-basic"></a><span data-ttu-id="2b92a-102">已宣告之項目的參考 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b92a-102">References to Declared Elements (Visual Basic)</span></span>

<span data-ttu-id="2b92a-103">當您的程式碼參考宣告的專案時，Visual Basic 的編譯器會將參考中的名稱與該名稱的適當宣告相符。</span><span class="sxs-lookup"><span data-stu-id="2b92a-103">When your code refers to a declared element, the Visual Basic compiler matches the name in your reference to the appropriate declaration of that name.</span></span> <span data-ttu-id="2b92a-104">如果以相同的名稱宣告一個以上的專案，您可以藉由 *限定* 其名稱來控制要參考哪些元素。</span><span class="sxs-lookup"><span data-stu-id="2b92a-104">If more than one element is declared with the same name, you can control which of those elements is to be referenced by *qualifying* its name.</span></span>  
  
 <span data-ttu-id="2b92a-105">編譯器會嘗試將名稱參考與最小 *範圍*的名稱宣告相符。</span><span class="sxs-lookup"><span data-stu-id="2b92a-105">The compiler attempts to match a name reference to a name declaration with the *narrowest scope*.</span></span> <span data-ttu-id="2b92a-106">這表示它會從進行參考的程式碼開始，並透過包含元素的連續層級向外運作。</span><span class="sxs-lookup"><span data-stu-id="2b92a-106">This means it starts with the code making the reference and works outward through successive levels of containing elements.</span></span>  
  
 <span data-ttu-id="2b92a-107">下列範例顯示兩個具有相同名稱之變數的參考。</span><span class="sxs-lookup"><span data-stu-id="2b92a-107">The following example shows references to two variables with the same name.</span></span> <span data-ttu-id="2b92a-108">此範例會在 `totalCount` 模組中的不同範圍層級宣告兩個變數，每個都命名為 `container` 。</span><span class="sxs-lookup"><span data-stu-id="2b92a-108">The example declares two variables, each named `totalCount`, at different levels of scope in module `container`.</span></span> <span data-ttu-id="2b92a-109">當程式 `showCount` 顯示 `totalCount` 但未限定時，Visual Basic 編譯器會以最小範圍（亦即內的區域宣告）解析宣告的參考 `showCount` 。</span><span class="sxs-lookup"><span data-stu-id="2b92a-109">When the procedure `showCount` displays `totalCount` without qualification, the Visual Basic compiler resolves the reference to the declaration with the narrowest scope, namely the local declaration inside `showCount`.</span></span> <span data-ttu-id="2b92a-110">當它符合 `totalCount` 包含的模組時 `container` ，編譯器會以更廣泛的範圍解析宣告的參考。</span><span class="sxs-lookup"><span data-stu-id="2b92a-110">When it qualifies `totalCount` with the containing module `container`, the compiler resolves the reference to the declaration with the broader scope.</span></span>  
  
```vb  
' Assume these two modules are both in the same assembly.  
Module container  
    Public totalCount As Integer = 1  
    Public Sub showCount()  
        Dim totalCount As Integer = 6000  
        ' The following statement displays the local totalCount (6000).  
        MsgBox("Unqualified totalCount is " & CStr(totalCount))  
        ' The following statement displays the module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
Module callingModule  
    Public Sub displayCount()  
        container.showCount()  
        ' The following statement displays the containing module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
```  
  
## <a name="qualifying-an-element-name"></a><span data-ttu-id="2b92a-111">限定元素名稱</span><span class="sxs-lookup"><span data-stu-id="2b92a-111">Qualifying an Element Name</span></span>  

 <span data-ttu-id="2b92a-112">如果您想要覆寫此搜尋程式並指定在更廣泛範圍中宣告的名稱，您必須使用更廣泛範圍的包含元素 *來限定* 名稱。</span><span class="sxs-lookup"><span data-stu-id="2b92a-112">If you want to override this search process and specify a name declared in a broader scope, you must *qualify* the name with the containing element of the broader scope.</span></span> <span data-ttu-id="2b92a-113">在某些情況下，您可能也必須限定包含元素。</span><span class="sxs-lookup"><span data-stu-id="2b92a-113">In some cases, you might also have to qualify the containing element.</span></span>  
  
 <span data-ttu-id="2b92a-114">限定名稱表示在來源語句中的前面加上識別目標元素定義位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="2b92a-114">Qualifying a name means preceding it in your source statement with information that identifies where the target element is defined.</span></span> <span data-ttu-id="2b92a-115">這項資訊稱為 *合格字串*。</span><span class="sxs-lookup"><span data-stu-id="2b92a-115">This information is called a *qualification string*.</span></span> <span data-ttu-id="2b92a-116">它可以包含一或多個命名空間、模組、類別或結構。</span><span class="sxs-lookup"><span data-stu-id="2b92a-116">It can include one or more namespaces and a module, class, or structure.</span></span>  
  
 <span data-ttu-id="2b92a-117">限定性字串應該明確地指定包含目標元素的模組、類別或結構。</span><span class="sxs-lookup"><span data-stu-id="2b92a-117">The qualification string should unambiguously specify the module, class, or structure containing the target element.</span></span> <span data-ttu-id="2b92a-118">容器可能會被放在另一個包含的元素中，通常是命名空間。</span><span class="sxs-lookup"><span data-stu-id="2b92a-118">The container might in turn be located in another containing element, usually a namespace.</span></span> <span data-ttu-id="2b92a-119">您可能需要在限定性字串中包含數個包含元素。</span><span class="sxs-lookup"><span data-stu-id="2b92a-119">You might need to include several containing elements in the qualification string.</span></span>  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a><span data-ttu-id="2b92a-120">藉由限定名稱來存取宣告的元素</span><span class="sxs-lookup"><span data-stu-id="2b92a-120">To access a declared element by qualifying its name</span></span>  
  
1. <span data-ttu-id="2b92a-121">判斷已定義元素的位置。</span><span class="sxs-lookup"><span data-stu-id="2b92a-121">Determine the location in which the element has been defined.</span></span> <span data-ttu-id="2b92a-122">這可能包括命名空間，或甚至是命名空間的階層。</span><span class="sxs-lookup"><span data-stu-id="2b92a-122">This might include a namespace, or even a hierarchy of namespaces.</span></span> <span data-ttu-id="2b92a-123">在最低層級的命名空間中，元素必須包含在模組、類別或結構中。</span><span class="sxs-lookup"><span data-stu-id="2b92a-123">Within the lowest-level namespace, the element must be contained in a module, class, or structure.</span></span>  
  
    ```vb  
    ' Assume the following hierarchy exists outside your code.  
    Namespace outerSpace  
        Namespace innerSpace  
            Module holdsTotals  
                Public Structure totals  
                    Public thisTotal As Integer  
                    Public Shared grandTotal As Long  
                End Structure  
            End Module  
        End Namespace  
    End Namespace  
    ```  
  
2. <span data-ttu-id="2b92a-124">根據目標元素的位置，判斷限定性路徑。</span><span class="sxs-lookup"><span data-stu-id="2b92a-124">Determine a qualification path based on the target element's location.</span></span> <span data-ttu-id="2b92a-125">從最高層級的命名空間開始，繼續進行最低層級的命名空間，並以包含目標元素的模組、類別或結構作為結尾。</span><span class="sxs-lookup"><span data-stu-id="2b92a-125">Start with the highest-level namespace, proceed to the lowest-level namespace, and end with the module, class, or structure containing the target element.</span></span> <span data-ttu-id="2b92a-126">路徑中的每個元素都必須包含其後的元素。</span><span class="sxs-lookup"><span data-stu-id="2b92a-126">Each element in the path must contain the element that follows it.</span></span>  
  
     <span data-ttu-id="2b92a-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span><span class="sxs-lookup"><span data-stu-id="2b92a-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span></span>  
  
3. <span data-ttu-id="2b92a-128">準備目標元素的限定性字串。</span><span class="sxs-lookup"><span data-stu-id="2b92a-128">Prepare the qualification string for the target element.</span></span> <span data-ttu-id="2b92a-129">在 `.` 路徑中的每個元素之後， () 放置句號。</span><span class="sxs-lookup"><span data-stu-id="2b92a-129">Place a period (`.`) after every element in the path.</span></span> <span data-ttu-id="2b92a-130">您的應用程式必須能夠存取您的限定性字串中的每個元素。</span><span class="sxs-lookup"><span data-stu-id="2b92a-130">Your application must have access to every element in your qualification string.</span></span>  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4. <span data-ttu-id="2b92a-131">以正常方式撰寫參考目標元素的運算式或指派語句。</span><span class="sxs-lookup"><span data-stu-id="2b92a-131">Write the expression or assignment statement referring to the target element in the normal way.</span></span>  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5. <span data-ttu-id="2b92a-132">在目標元素名稱之前加上限定性字串。</span><span class="sxs-lookup"><span data-stu-id="2b92a-132">Precede the target element name with the qualification string.</span></span> <span data-ttu-id="2b92a-133">名稱應該緊接在 `.` 包含元素的模組、類別或結構後面的期間 () 。</span><span class="sxs-lookup"><span data-stu-id="2b92a-133">The name should immediately follow the period (`.`) that follows the module, class, or structure that contains the element.</span></span>  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6. <span data-ttu-id="2b92a-134">編譯器會使用限定性字串來尋找明確的明確宣告，使其符合目標元素參考。</span><span class="sxs-lookup"><span data-stu-id="2b92a-134">The compiler uses the qualification string to find a clear, unambiguous declaration to which it can match the target element reference.</span></span>  
  
 <span data-ttu-id="2b92a-135">如果您的應用程式可以存取多個名稱相同的程式設計項目，您可能也必須限定名稱參考。</span><span class="sxs-lookup"><span data-stu-id="2b92a-135">You might also have to qualify a name reference if your application has access to more than one programming element that has the same name.</span></span> <span data-ttu-id="2b92a-136">例如， <xref:System.Windows.Forms> 和 <xref:System.Web.UI.WebControls> 命名空間都包含 `Label` 類別 (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> 和 <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>) 。</span><span class="sxs-lookup"><span data-stu-id="2b92a-136">For example, the <xref:System.Windows.Forms> and <xref:System.Web.UI.WebControls> namespaces both contain a `Label` class (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>).</span></span> <span data-ttu-id="2b92a-137">如果您的應用程式使用兩者，或它定義自己的 `Label` 類別，您必須區分不同的 `Label` 物件。</span><span class="sxs-lookup"><span data-stu-id="2b92a-137">If your application uses both, or if it defines its own `Label` class, you must distinguish the different `Label` objects.</span></span> <span data-ttu-id="2b92a-138">在變數宣告中包含命名空間或匯入別名。</span><span class="sxs-lookup"><span data-stu-id="2b92a-138">Include the namespace or import alias in the variable declaration.</span></span> <span data-ttu-id="2b92a-139">下列範例會使用匯入別名。</span><span class="sxs-lookup"><span data-stu-id="2b92a-139">The following example uses the import alias.</span></span>  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a><span data-ttu-id="2b92a-140">其他包含元素的成員</span><span class="sxs-lookup"><span data-stu-id="2b92a-140">Members of Other Containing Elements</span></span>  

 <span data-ttu-id="2b92a-141">當您使用其他類別或結構的非共用成員時，您必須先使用指向類別或結構實例的變數或運算式來限定成員名稱。</span><span class="sxs-lookup"><span data-stu-id="2b92a-141">When you use a nonshared member of another class or structure, you must first qualify the member name with a variable or expression that points to an instance of the class or structure.</span></span> <span data-ttu-id="2b92a-142">在下列範例中， `demoClass` 是名為之類別的實例 `class1` 。</span><span class="sxs-lookup"><span data-stu-id="2b92a-142">In the following example, `demoClass` is an instance of a class named `class1`.</span></span>  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 <span data-ttu-id="2b92a-143">您無法使用類別名稱本身來限定未 [共用](../../../language-reference/modifiers/shared.md)的成員。</span><span class="sxs-lookup"><span data-stu-id="2b92a-143">You cannot use the class name itself to qualify a member that is not [Shared](../../../language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="2b92a-144">在此情況下，您必須先在物件變數中建立實例 (`demoClass`) 然後依變數名稱來參考它。</span><span class="sxs-lookup"><span data-stu-id="2b92a-144">You must first create an instance in an object variable (in this case `demoClass`) and then reference it by the variable name.</span></span>  
  
 <span data-ttu-id="2b92a-145">如果類別或結構具有 `Shared` 成員，您可以使用類別或結構名稱或指向實例的變數或運算式來限定該成員。</span><span class="sxs-lookup"><span data-stu-id="2b92a-145">If a class or structure has a `Shared` member, you can qualify that member either with the class or structure name or with a variable or expression that points to an instance.</span></span>  
  
 <span data-ttu-id="2b92a-146">模組沒有任何個別的實例，而且其所有成員 `Shared` 預設為。</span><span class="sxs-lookup"><span data-stu-id="2b92a-146">A module does not have any separate instances, and all its members are `Shared` by default.</span></span> <span data-ttu-id="2b92a-147">因此，您可以使用模組名稱來限定模組成員。</span><span class="sxs-lookup"><span data-stu-id="2b92a-147">Therefore, you qualify a module member with the module name.</span></span>  
  
 <span data-ttu-id="2b92a-148">下列範例會顯示模組成員程式的限定參考。</span><span class="sxs-lookup"><span data-stu-id="2b92a-148">The following example shows qualified references to module member procedures.</span></span> <span data-ttu-id="2b92a-149">此範例會在專案中的不同模組中宣告兩個 `Sub` 程式，兩者都有兩個名稱 `perform` 。</span><span class="sxs-lookup"><span data-stu-id="2b92a-149">The example declares two `Sub` procedures, both named `perform`, in different modules in a project.</span></span> <span data-ttu-id="2b92a-150">您可以指定每一個，而不需要在其本身的模組內進行限定性，但如果從任何其他地方參考，則必須限定。</span><span class="sxs-lookup"><span data-stu-id="2b92a-150">Each one can be specified without qualification within its own module but must be qualified if referenced from anywhere else.</span></span> <span data-ttu-id="2b92a-151">因為中的最後一個參考 `module3` 不符合資格 `perform` ，所以編譯器無法解析該參考。</span><span class="sxs-lookup"><span data-stu-id="2b92a-151">Because the final reference in `module3` does not qualify `perform`, the compiler cannot resolve that reference.</span></span>  
  
```vb  
' Assume these three modules are all in the same assembly.  
Module module1  
    Public Sub perform()  
        MsgBox("module1.perform() now returning")  
    End Sub  
End Module  
Module module2  
    Public Sub perform()  
        MsgBox("module2.perform() now returning")  
    End Sub  
    Public Sub doSomething()  
        ' The following statement calls perform in module2, the active module.  
        perform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
    End Sub  
End Module  
Module module3  
    Public Sub callPerform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
        ' The following statement makes an unresolvable name reference  
        ' and therefore generates a COMPILER ERROR.  
        perform() ' INVALID statement  
    End Sub  
End Module  
```  
  
## <a name="references-to-projects"></a><span data-ttu-id="2b92a-152">專案的參考</span><span class="sxs-lookup"><span data-stu-id="2b92a-152">References to Projects</span></span>  

 <span data-ttu-id="2b92a-153">若要使用其他專案中定義的 [公用](../../../language-reference/modifiers/public.md) 元素，您必須先設定該專案元件或型別程式庫的 *參考* 。</span><span class="sxs-lookup"><span data-stu-id="2b92a-153">To use [Public](../../../language-reference/modifiers/public.md) elements defined in another project, you must first set a *reference* to that project's assembly or type library.</span></span> <span data-ttu-id="2b92a-154">若要設定參考，請按一下 [**專案**] 功能表上的 [**加入參考**]，或使用[-reference (Visual Basic) ](../../../reference/command-line-compiler/reference.md)命令列編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="2b92a-154">To set a reference, click **Add Reference** on the **Project** menu, or use the [-reference (Visual Basic)](../../../reference/command-line-compiler/reference.md) command-line compiler option.</span></span>  
  
 <span data-ttu-id="2b92a-155">例如，您可以使用 .NET Framework 的 XML 物件模型。</span><span class="sxs-lookup"><span data-stu-id="2b92a-155">For example, you can use the XML object model of the .NET Framework.</span></span> <span data-ttu-id="2b92a-156">如果您設定命名空間的參考 <xref:System.Xml> ，您可以宣告並使用其任何類別，例如 <xref:System.Xml.XmlDocument> 。</span><span class="sxs-lookup"><span data-stu-id="2b92a-156">If you set a reference to the <xref:System.Xml> namespace, you can declare and use any of its classes, such as <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="2b92a-157">下列範例會使用 <xref:System.Xml.XmlDocument>。</span><span class="sxs-lookup"><span data-stu-id="2b92a-157">The following example uses <xref:System.Xml.XmlDocument>.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a><span data-ttu-id="2b92a-158">匯入包含元素</span><span class="sxs-lookup"><span data-stu-id="2b92a-158">Importing Containing Elements</span></span>  

 <span data-ttu-id="2b92a-159">您可以使用 [Imports 語句 ( .Net 命名空間，並輸入) ](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) 匯 *入* 包含您要使用之模組或類別的命名空間。</span><span class="sxs-lookup"><span data-stu-id="2b92a-159">You can use the [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) to *import* the namespaces that contain the modules or classes that you want to use.</span></span> <span data-ttu-id="2b92a-160">這可讓您參考匯入之命名空間中定義的元素，而不需要完整限定其名稱。</span><span class="sxs-lookup"><span data-stu-id="2b92a-160">This enables you to refer to the elements defined in an imported namespace without fully qualifying their names.</span></span> <span data-ttu-id="2b92a-161">下列範例會重寫先前的範例，以匯入 <xref:System.Xml> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="2b92a-161">The following example rewrites the previous example to import the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 <span data-ttu-id="2b92a-162">此外， `Imports` 語句可以針對每個匯入的命名空間定義匯 *入別名* 。</span><span class="sxs-lookup"><span data-stu-id="2b92a-162">In addition, the `Imports` statement can define an *import alias* for each imported namespace.</span></span> <span data-ttu-id="2b92a-163">這可讓原始程式碼變得更短且更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="2b92a-163">This can make the source code shorter and easier to read.</span></span> <span data-ttu-id="2b92a-164">下列範例會重寫先前的範例，以 `xD` 做為 <xref:System.Xml> 命名空間的別名。</span><span class="sxs-lookup"><span data-stu-id="2b92a-164">The following example rewrites the previous example to use `xD` as an alias for the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 <span data-ttu-id="2b92a-165">`Imports`語句不會將其他專案中的元素提供給您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2b92a-165">The `Imports` statement does not make elements from other projects available to your application.</span></span> <span data-ttu-id="2b92a-166">也就是說，它不會取代設定參考。</span><span class="sxs-lookup"><span data-stu-id="2b92a-166">That is, it does not take the place of setting a reference.</span></span> <span data-ttu-id="2b92a-167">匯入命名空間只會移除限定該命名空間中定義之名稱的需求。</span><span class="sxs-lookup"><span data-stu-id="2b92a-167">Importing a namespace just removes the requirement to qualify the names defined in that namespace.</span></span>  
  
 <span data-ttu-id="2b92a-168">您也可以使用 `Imports` 語句來匯入模組、類別、結構和列舉。</span><span class="sxs-lookup"><span data-stu-id="2b92a-168">You can also use the `Imports` statement to import modules, classes, structures, and enumerations.</span></span> <span data-ttu-id="2b92a-169">然後，您可以使用這類匯入專案的成員，而不需限定。</span><span class="sxs-lookup"><span data-stu-id="2b92a-169">You can then use the members of such imported elements without qualification.</span></span> <span data-ttu-id="2b92a-170">不過，您必須一律使用評估為類別或結構實例的變數或運算式，來限定類別和結構的非共用成員。</span><span class="sxs-lookup"><span data-stu-id="2b92a-170">However, you must always qualify nonshared members of classes and structures with a variable or expression that evaluates to an instance of the class or structure.</span></span>  
  
## <a name="naming-guidelines"></a><span data-ttu-id="2b92a-171">命名方針</span><span class="sxs-lookup"><span data-stu-id="2b92a-171">Naming Guidelines</span></span>  

 <span data-ttu-id="2b92a-172">當您定義兩個以上具有相同名稱的程式設計專案時，當編譯器嘗試解析該名稱的參考時，可能會產生不 *明確的名稱* 。</span><span class="sxs-lookup"><span data-stu-id="2b92a-172">When you define two or more programming elements that have the same name, a *name ambiguity* can result when the compiler attempts to resolve a reference to that name.</span></span> <span data-ttu-id="2b92a-173">如果範圍內有一個以上的定義，或如果沒有定義在範圍內，則參考為兩難。</span><span class="sxs-lookup"><span data-stu-id="2b92a-173">If more than one definition is in scope, or if no definition is in scope, the reference is irresolvable.</span></span> <span data-ttu-id="2b92a-174">如需範例，請參閱此說明頁面上的「限定參考範例」。</span><span class="sxs-lookup"><span data-stu-id="2b92a-174">For an example, see "Qualified Reference Example" on this Help page.</span></span>  
  
 <span data-ttu-id="2b92a-175">您可以提供所有元素的唯一名稱，以避免名稱不明確。</span><span class="sxs-lookup"><span data-stu-id="2b92a-175">You can avoid name ambiguity by giving all your elements unique names.</span></span> <span data-ttu-id="2b92a-176">然後，您可以參考任何專案，而不需要使用命名空間、模組或類別來限定其名稱。</span><span class="sxs-lookup"><span data-stu-id="2b92a-176">Then you can make reference to any element without having to qualify its name with a namespace, module, or class.</span></span> <span data-ttu-id="2b92a-177">您也可以減少不慎參考錯誤元素的機會。</span><span class="sxs-lookup"><span data-stu-id="2b92a-177">You also reduce the chances of accidentally referring to the wrong element.</span></span>  
  
## <a name="shadowing"></a><span data-ttu-id="2b92a-178">遮蔽</span><span class="sxs-lookup"><span data-stu-id="2b92a-178">Shadowing</span></span>  

 <span data-ttu-id="2b92a-179">當兩個程式設計專案共用相同的名稱時，其中一個元素可以隱藏或 *遮蔽*另一個。</span><span class="sxs-lookup"><span data-stu-id="2b92a-179">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="2b92a-180">無法參考遮蔽的元素;相反地，當您的程式碼使用已遮蔽的元素名稱時，Visual Basic 編譯器會將它解析成遮蔽專案。</span><span class="sxs-lookup"><span data-stu-id="2b92a-180">A shadowed element is not available for reference; instead, when your code uses the shadowed element name, the Visual Basic compiler resolves it to the shadowing element.</span></span> <span data-ttu-id="2b92a-181">如需範例的詳細說明，請參閱 [Visual Basic 中的遮蔽](shadowing.md)。</span><span class="sxs-lookup"><span data-stu-id="2b92a-181">For a more detailed explanation with examples, see [Shadowing in Visual Basic](shadowing.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b92a-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b92a-182">See also</span></span>

- [<span data-ttu-id="2b92a-183">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="2b92a-183">Declared Element Names</span></span>](declared-element-names.md)
- [<span data-ttu-id="2b92a-184">宣告項目特性</span><span class="sxs-lookup"><span data-stu-id="2b92a-184">Declared Element Characteristics</span></span>](declared-element-characteristics.md)
- [<span data-ttu-id="2b92a-185">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="2b92a-185">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="2b92a-186">變數</span><span class="sxs-lookup"><span data-stu-id="2b92a-186">Variables</span></span>](../variables/index.md)
- [<span data-ttu-id="2b92a-187">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="2b92a-187">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="2b92a-188">New 運算子</span><span class="sxs-lookup"><span data-stu-id="2b92a-188">New Operator</span></span>](../../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="2b92a-189">公開</span><span class="sxs-lookup"><span data-stu-id="2b92a-189">Public</span></span>](../../../language-reference/modifiers/public.md)
