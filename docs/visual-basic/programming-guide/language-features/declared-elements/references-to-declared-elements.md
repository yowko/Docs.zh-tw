---
title: 已宣告之項目的參考 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: 0fca02ab2dcb507c1129f18f31a25c7809fc9710
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917952"
---
# <a name="references-to-declared-elements-visual-basic"></a><span data-ttu-id="72f19-102">已宣告之項目的參考 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72f19-102">References to Declared Elements (Visual Basic)</span></span>
<span data-ttu-id="72f19-103">當您的程式碼參考宣告的項目時，Visual Basic 編譯器會符合您適當的宣告該名稱的參考中的名稱。</span><span class="sxs-lookup"><span data-stu-id="72f19-103">When your code refers to a declared element, the Visual Basic compiler matches the name in your reference to the appropriate declaration of that name.</span></span> <span data-ttu-id="72f19-104">如果多個項目宣告具有相同名稱時，您可以控制這些項目所要參考即*合格*它的名稱。</span><span class="sxs-lookup"><span data-stu-id="72f19-104">If more than one element is declared with the same name, you can control which of those elements is to be referenced by *qualifying* its name.</span></span>  
  
 <span data-ttu-id="72f19-105">編譯器會嘗試比對的名稱宣告的名稱參考*最小範圍*。</span><span class="sxs-lookup"><span data-stu-id="72f19-105">The compiler attempts to match a name reference to a name declaration with the *narrowest scope*.</span></span> <span data-ttu-id="72f19-106">這表示它在製作該參考的程式碼的開頭，並透過連續層級的包含項目向外運作。</span><span class="sxs-lookup"><span data-stu-id="72f19-106">This means it starts with the code making the reference and works outward through successive levels of containing elements.</span></span>  
  
 <span data-ttu-id="72f19-107">下列範例顯示兩個變數具有相同名稱的參考。</span><span class="sxs-lookup"><span data-stu-id="72f19-107">The following example shows references to two variables with the same name.</span></span> <span data-ttu-id="72f19-108">此範例會宣告兩個變數，每個具名`totalCount`，在模組範圍的不同層級`container`。</span><span class="sxs-lookup"><span data-stu-id="72f19-108">The example declares two variables, each named `totalCount`, at different levels of scope in module `container`.</span></span> <span data-ttu-id="72f19-109">當此程序`showCount`會顯示`totalCount`無限制，Visual Basic 編譯器會參考解析為具有最小的範圍，也就是在本機宣告的宣告`showCount`。</span><span class="sxs-lookup"><span data-stu-id="72f19-109">When the procedure `showCount` displays `totalCount` without qualification, the Visual Basic compiler resolves the reference to the declaration with the narrowest scope, namely the local declaration inside `showCount`.</span></span> <span data-ttu-id="72f19-110">當符合`totalCount`所包含的模組與`container`，編譯器會解析至具有較廣的範圍宣告的參考。</span><span class="sxs-lookup"><span data-stu-id="72f19-110">When it qualifies `totalCount` with the containing module `container`, the compiler resolves the reference to the declaration with the broader scope.</span></span>  
  
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
  
## <a name="qualifying-an-element-name"></a><span data-ttu-id="72f19-111">限定項目名稱</span><span class="sxs-lookup"><span data-stu-id="72f19-111">Qualifying an Element Name</span></span>  
 <span data-ttu-id="72f19-112">如果您想要覆寫此搜尋程序並指定名稱的宣告是在更廣泛的範圍內，而您必須*限定*包含的項目，較廣範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="72f19-112">If you want to override this search process and specify a name declared in a broader scope, you must *qualify* the name with the containing element of the broader scope.</span></span> <span data-ttu-id="72f19-113">在某些情況下，您可能也必須符合 包含的項目。</span><span class="sxs-lookup"><span data-stu-id="72f19-113">In some cases, you might also have to qualify the containing element.</span></span>  
  
 <span data-ttu-id="72f19-114">限定名稱表示您的來源陳述式資訊識別其中定義目標項目中在它前面。</span><span class="sxs-lookup"><span data-stu-id="72f19-114">Qualifying a name means preceding it in your source statement with information that identifies where the target element is defined.</span></span> <span data-ttu-id="72f19-115">這項資訊會呼叫*限定性條件字串*。</span><span class="sxs-lookup"><span data-stu-id="72f19-115">This information is called a *qualification string*.</span></span> <span data-ttu-id="72f19-116">它可以包含一或多個命名空間和模組，這是類別或結構。</span><span class="sxs-lookup"><span data-stu-id="72f19-116">It can include one or more namespaces and a module, class, or structure.</span></span>  
  
 <span data-ttu-id="72f19-117">模組、 類別或結構，其中包含目標項目，應該明確地指定限定性條件字串。</span><span class="sxs-lookup"><span data-stu-id="72f19-117">The qualification string should unambiguously specify the module, class, or structure containing the target element.</span></span> <span data-ttu-id="72f19-118">容器接著可能位於另一個包含項目，通常是命名空間。</span><span class="sxs-lookup"><span data-stu-id="72f19-118">The container might in turn be located in another containing element, usually a namespace.</span></span> <span data-ttu-id="72f19-119">您可能需要限定性條件字串中包含數個包含的項目。</span><span class="sxs-lookup"><span data-stu-id="72f19-119">You might need to include several containing elements in the qualification string.</span></span>  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a><span data-ttu-id="72f19-120">若要限定其名稱來存取宣告的項目</span><span class="sxs-lookup"><span data-stu-id="72f19-120">To access a declared element by qualifying its name</span></span>  
  
1. <span data-ttu-id="72f19-121">判斷已定義的項目所在的位置。</span><span class="sxs-lookup"><span data-stu-id="72f19-121">Determine the location in which the element has been defined.</span></span> <span data-ttu-id="72f19-122">這可能包括命名空間或甚至是命名空間的階層。</span><span class="sxs-lookup"><span data-stu-id="72f19-122">This might include a namespace, or even a hierarchy of namespaces.</span></span> <span data-ttu-id="72f19-123">最低層級命名空間內的項目必須包含在模組、 類別或結構。</span><span class="sxs-lookup"><span data-stu-id="72f19-123">Within the lowest-level namespace, the element must be contained in a module, class, or structure.</span></span>  
  
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
  
2. <span data-ttu-id="72f19-124">判斷限定性條件路徑，根據目標項目的位置。</span><span class="sxs-lookup"><span data-stu-id="72f19-124">Determine a qualification path based on the target element's location.</span></span> <span data-ttu-id="72f19-125">開始使用的最高層級的命名空間，繼續在最低層級命名空間中，且結尾模組、 類別或結構，其中包含目標項目。</span><span class="sxs-lookup"><span data-stu-id="72f19-125">Start with the highest-level namespace, proceed to the lowest-level namespace, and end with the module, class, or structure containing the target element.</span></span> <span data-ttu-id="72f19-126">在路徑中的每個項目必須包含在它後面的項目。</span><span class="sxs-lookup"><span data-stu-id="72f19-126">Each element in the path must contain the element that follows it.</span></span>  
  
     <span data-ttu-id="72f19-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span><span class="sxs-lookup"><span data-stu-id="72f19-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span></span>  
  
3. <span data-ttu-id="72f19-128">準備目標項目的限定性條件字串。</span><span class="sxs-lookup"><span data-stu-id="72f19-128">Prepare the qualification string for the target element.</span></span> <span data-ttu-id="72f19-129">將句號 (`.`) 後的路徑中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="72f19-129">Place a period (`.`) after every element in the path.</span></span> <span data-ttu-id="72f19-130">應用程式必須具有限定性條件字串中的每個項目的存取權。</span><span class="sxs-lookup"><span data-stu-id="72f19-130">Your application must have access to every element in your qualification string.</span></span>  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4. <span data-ttu-id="72f19-131">撰寫運算式或指派陳述式以一般方式參考目標項目。</span><span class="sxs-lookup"><span data-stu-id="72f19-131">Write the expression or assignment statement referring to the target element in the normal way.</span></span>  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5. <span data-ttu-id="72f19-132">目標項目名稱前加限定性條件字串。</span><span class="sxs-lookup"><span data-stu-id="72f19-132">Precede the target element name with the qualification string.</span></span> <span data-ttu-id="72f19-133">名稱應該立即接在句號 (`.`)，跟模組、 類別或結構，其包含的項目。</span><span class="sxs-lookup"><span data-stu-id="72f19-133">The name should immediately follow the period (`.`) that follows the module, class, or structure that contains the element.</span></span>  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6. <span data-ttu-id="72f19-134">編譯器會用來尋找要符合目標項目參考的清楚且明確宣告的限定性條件字串。</span><span class="sxs-lookup"><span data-stu-id="72f19-134">The compiler uses the qualification string to find a clear, unambiguous declaration to which it can match the target element reference.</span></span>  
  
 <span data-ttu-id="72f19-135">您也可能必須限定名稱參考，如果您的應用程式可以存取多個具有相同名稱的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="72f19-135">You might also have to qualify a name reference if your application has access to more than one programming element that has the same name.</span></span> <span data-ttu-id="72f19-136">例如，<xref:System.Windows.Forms>並<xref:System.Web.UI.WebControls>這兩個的命名空間包含`Label`類別 (<xref:System.Windows.Forms.Label?displayProperty=nameWithType>和<xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="72f19-136">For example, the <xref:System.Windows.Forms> and <xref:System.Web.UI.WebControls> namespaces both contain a `Label` class (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>).</span></span> <span data-ttu-id="72f19-137">如果您的應用程式同時使用兩者，則它會定義它自己`Label`類別，您必須以不同的方式區分`Label`物件。</span><span class="sxs-lookup"><span data-stu-id="72f19-137">If your application uses both, or if it defines its own `Label` class, you must distinguish the different `Label` objects.</span></span> <span data-ttu-id="72f19-138">在變數宣告中包含的命名空間或匯入的別名。</span><span class="sxs-lookup"><span data-stu-id="72f19-138">Include the namespace or import alias in the variable declaration.</span></span> <span data-ttu-id="72f19-139">下列範例會使用匯入別名。</span><span class="sxs-lookup"><span data-stu-id="72f19-139">The following example uses the import alias.</span></span>  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a><span data-ttu-id="72f19-140">成員的其他包含項目</span><span class="sxs-lookup"><span data-stu-id="72f19-140">Members of Other Containing Elements</span></span>  
 <span data-ttu-id="72f19-141">當您使用另一個類別或結構的非共用的成員時，您必須先限定成員名稱與變數或運算式，以指向類別或結構的執行個體。</span><span class="sxs-lookup"><span data-stu-id="72f19-141">When you use a nonshared member of another class or structure, you must first qualify the member name with a variable or expression that points to an instance of the class or structure.</span></span> <span data-ttu-id="72f19-142">在下列範例中，`demoClass`是一個名為類別的執行個體`class1`。</span><span class="sxs-lookup"><span data-stu-id="72f19-142">In the following example, `demoClass` is an instance of a class named `class1`.</span></span>  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 <span data-ttu-id="72f19-143">您無法使用類別名稱本身來限定成員不是[共用](../../../../visual-basic/language-reference/modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="72f19-143">You cannot use the class name itself to qualify a member that is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="72f19-144">您必須先建立執行個體中的物件變數 (在此情況下`demoClass`)，然後依變數名稱參考它。</span><span class="sxs-lookup"><span data-stu-id="72f19-144">You must first create an instance in an object variable (in this case `demoClass`) and then reference it by the variable name.</span></span>  
  
 <span data-ttu-id="72f19-145">如果類別或結構具有`Shared`成員，您可以限定的類別或結構名稱或變數或運算式，以指向執行個體與該成員。</span><span class="sxs-lookup"><span data-stu-id="72f19-145">If a class or structure has a `Shared` member, you can qualify that member either with the class or structure name or with a variable or expression that points to an instance.</span></span>  
  
 <span data-ttu-id="72f19-146">模組沒有任何個別的執行個體和其所有成員都是`Shared`預設。</span><span class="sxs-lookup"><span data-stu-id="72f19-146">A module does not have any separate instances, and all its members are `Shared` by default.</span></span> <span data-ttu-id="72f19-147">因此，您符合資格的模組名稱的模組成員。</span><span class="sxs-lookup"><span data-stu-id="72f19-147">Therefore, you qualify a module member with the module name.</span></span>  
  
 <span data-ttu-id="72f19-148">下列範例會顯示模組成員程序的完整的參考。</span><span class="sxs-lookup"><span data-stu-id="72f19-148">The following example shows qualified references to module member procedures.</span></span> <span data-ttu-id="72f19-149">此範例會宣告兩個`Sub`程序中，具名`perform`，在專案中的不同模組中。</span><span class="sxs-lookup"><span data-stu-id="72f19-149">The example declares two `Sub` procedures, both named `perform`, in different modules in a project.</span></span> <span data-ttu-id="72f19-150">每一個可以指定無限制地在自己的模組，但必須是名稱，如果從其他位置參考。</span><span class="sxs-lookup"><span data-stu-id="72f19-150">Each one can be specified without qualification within its own module but must be qualified if referenced from anywhere else.</span></span> <span data-ttu-id="72f19-151">因為參考中的最終`module3`不會限定`perform`，編譯器無法解析的參考。</span><span class="sxs-lookup"><span data-stu-id="72f19-151">Because the final reference in `module3` does not qualify `perform`, the compiler cannot resolve that reference.</span></span>  
  
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
  
## <a name="references-to-projects"></a><span data-ttu-id="72f19-152">專案的參考</span><span class="sxs-lookup"><span data-stu-id="72f19-152">References to Projects</span></span>  
 <span data-ttu-id="72f19-153">若要使用[公開金鑰](../../../../visual-basic/language-reference/modifiers/public.md)定義另一個專案中的項目，您必須先設定*參考*至該專案的組件或類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="72f19-153">To use [Public](../../../../visual-basic/language-reference/modifiers/public.md) elements defined in another project, you must first set a *reference* to that project's assembly or type library.</span></span> <span data-ttu-id="72f19-154">若要設定的參考，按一下**加入參考**上**專案**功能表上或使用[/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md)命令列編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="72f19-154">To set a reference, click **Add Reference** on the **Project** menu, or use the [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) command-line compiler option.</span></span>  
  
 <span data-ttu-id="72f19-155">例如，您可以使用的 XML 物件模型[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="72f19-155">For example, you can use the XML object model of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="72f19-156">如果您將參考設定為<xref:System.Xml>命名空間中，您可以宣告並使用任何其類別，例如<xref:System.Xml.XmlDocument>。</span><span class="sxs-lookup"><span data-stu-id="72f19-156">If you set a reference to the <xref:System.Xml> namespace, you can declare and use any of its classes, such as <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="72f19-157">下列範例會使用<xref:System.Xml.XmlDocument>。</span><span class="sxs-lookup"><span data-stu-id="72f19-157">The following example uses <xref:System.Xml.XmlDocument>.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a><span data-ttu-id="72f19-158">匯入包含項目</span><span class="sxs-lookup"><span data-stu-id="72f19-158">Importing Containing Elements</span></span>  
 <span data-ttu-id="72f19-159">您可以使用[Imports 陳述式 （.NET 命名空間和類型）](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)要*匯入*命名空間包含的模組或您想要使用的類別。</span><span class="sxs-lookup"><span data-stu-id="72f19-159">You can use the [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to *import* the namespaces that contain the modules or classes that you want to use.</span></span> <span data-ttu-id="72f19-160">這可讓您匯入的命名空間中定義，而不必完整限定其名稱的項目參考。</span><span class="sxs-lookup"><span data-stu-id="72f19-160">This enables you to refer to the elements defined in an imported namespace without fully qualifying their names.</span></span> <span data-ttu-id="72f19-161">下列範例重寫上述範例若要匯入<xref:System.Xml>命名空間。</span><span class="sxs-lookup"><span data-stu-id="72f19-161">The following example rewrites the previous example to import the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 <span data-ttu-id="72f19-162">颾魤 ㄛ`Imports`陳述式可定義*匯入別名*每個匯入的命名空間。</span><span class="sxs-lookup"><span data-stu-id="72f19-162">In addition, the `Imports` statement can define an *import alias* for each imported namespace.</span></span> <span data-ttu-id="72f19-163">這可讓較短且更容易讀取的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="72f19-163">This can make the source code shorter and easier to read.</span></span> <span data-ttu-id="72f19-164">下列範例重寫上一個範例中使用`xD`做為別名<xref:System.Xml>命名空間。</span><span class="sxs-lookup"><span data-stu-id="72f19-164">The following example rewrites the previous example to use `xD` as an alias for the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 <span data-ttu-id="72f19-165">`Imports`陳述式不會從其他專案項目提供您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="72f19-165">The `Imports` statement does not make elements from other projects available to your application.</span></span> <span data-ttu-id="72f19-166">也就是說，它不會取代設定的參考。</span><span class="sxs-lookup"><span data-stu-id="72f19-166">That is, it does not take the place of setting a reference.</span></span> <span data-ttu-id="72f19-167">只匯入命名空間，就不需要限定該命名空間中定義的名稱。</span><span class="sxs-lookup"><span data-stu-id="72f19-167">Importing a namespace just removes the requirement to qualify the names defined in that namespace.</span></span>  
  
 <span data-ttu-id="72f19-168">您也可以使用`Imports`陳述式匯入模組、 類別、 結構和列舉型別。</span><span class="sxs-lookup"><span data-stu-id="72f19-168">You can also use the `Imports` statement to import modules, classes, structures, and enumerations.</span></span> <span data-ttu-id="72f19-169">然後，您可以使用這類匯入的項目，但是不限定的成員。</span><span class="sxs-lookup"><span data-stu-id="72f19-169">You can then use the members of such imported elements without qualification.</span></span> <span data-ttu-id="72f19-170">不過，您一律必須限定非共用的成員的類別和結構變數或運算式評估為類別或結構的執行個體。</span><span class="sxs-lookup"><span data-stu-id="72f19-170">However, you must always qualify nonshared members of classes and structures with a variable or expression that evaluates to an instance of the class or structure.</span></span>  
  
## <a name="naming-guidelines"></a><span data-ttu-id="72f19-171">命名方針</span><span class="sxs-lookup"><span data-stu-id="72f19-171">Naming Guidelines</span></span>  
 <span data-ttu-id="72f19-172">當您定義兩個或多個具有相同的名稱，程式設計項目*名稱模稜兩可*可能會造成當編譯器嘗試解析該名稱的參考。</span><span class="sxs-lookup"><span data-stu-id="72f19-172">When you define two or more programming elements that have the same name, a *name ambiguity* can result when the compiler attempts to resolve a reference to that name.</span></span> <span data-ttu-id="72f19-173">如果多個定義在範圍內，或如果沒有定義在範圍內，是無法解析的參考。</span><span class="sxs-lookup"><span data-stu-id="72f19-173">If more than one definition is in scope, or if no definition is in scope, the reference is irresolvable.</span></span> <span data-ttu-id="72f19-174">如需範例，請參閱此說明頁面上的 < 限定參考範例 >。</span><span class="sxs-lookup"><span data-stu-id="72f19-174">For an example, see "Qualified Reference Example" on this Help page.</span></span>  
  
 <span data-ttu-id="72f19-175">您可以為您的所有項目指定唯一的名稱，以避免名稱模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="72f19-175">You can avoid name ambiguity by giving all your elements unique names.</span></span> <span data-ttu-id="72f19-176">然後您可以讓任何項目的參考，而不需要限定其名稱與命名空間、 模組或類別。</span><span class="sxs-lookup"><span data-stu-id="72f19-176">Then you can make reference to any element without having to qualify its name with a namespace, module, or class.</span></span> <span data-ttu-id="72f19-177">您也會減少不小心參考到錯誤的元素的機會。</span><span class="sxs-lookup"><span data-stu-id="72f19-177">You also reduce the chances of accidentally referring to the wrong element.</span></span>  
  
## <a name="shadowing"></a><span data-ttu-id="72f19-178">遮蔽</span><span class="sxs-lookup"><span data-stu-id="72f19-178">Shadowing</span></span>  
 <span data-ttu-id="72f19-179">當兩個程式設計項目共用相同的名稱時，可以隱藏其中一個，或是*陰影*，另一個。</span><span class="sxs-lookup"><span data-stu-id="72f19-179">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="72f19-180">遮蔽的項目不是可供參考。相反地，當您的程式碼使用遮蔽的項目名稱時，Visual Basic 編譯器解析遮蔽的項目。</span><span class="sxs-lookup"><span data-stu-id="72f19-180">A shadowed element is not available for reference; instead, when your code uses the shadowed element name, the Visual Basic compiler resolves it to the shadowing element.</span></span> <span data-ttu-id="72f19-181">如範例的更詳細說明，請參閱 < [Visual Basic 中的遮蔽功能](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。</span><span class="sxs-lookup"><span data-stu-id="72f19-181">For a more detailed explanation with examples, see [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72f19-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72f19-182">See also</span></span>

- [<span data-ttu-id="72f19-183">宣告項目名稱</span><span class="sxs-lookup"><span data-stu-id="72f19-183">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="72f19-184">宣告項目特性</span><span class="sxs-lookup"><span data-stu-id="72f19-184">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="72f19-185">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="72f19-185">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="72f19-186">變數</span><span class="sxs-lookup"><span data-stu-id="72f19-186">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="72f19-187">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="72f19-187">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="72f19-188">New 運算子</span><span class="sxs-lookup"><span data-stu-id="72f19-188">New Operator</span></span>](../../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="72f19-189">Public</span><span class="sxs-lookup"><span data-stu-id="72f19-189">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)
