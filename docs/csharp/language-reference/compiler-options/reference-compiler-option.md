---
title: -reference (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /reference
helpviewer_keywords:
- /r compiler option [C#]
- reference compiler option [C#]
- r compiler option [C#]
- /reference compiler option [C#]
- -r compiler option [C#]
- metadata import [C#]
- public type information [C#]
- -reference compiler option [C#]
ms.assetid: 8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4
ms.openlocfilehash: fbf93a87cede753ebd41c148f4fb4bb761846954
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593077"
---
# <a name="-reference-c-compiler-options"></a><span data-ttu-id="ec593-102">-reference (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="ec593-102">-reference (C# Compiler Options)</span></span>
<span data-ttu-id="ec593-103">**-reference** 選項可讓編譯器將指定檔案的 [public](../../../csharp/language-reference/keywords/public.md) 類型資訊匯入至目前的專案，以讓您透過指定的組件檔案來參考中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ec593-103">The **-reference** option causes the compiler to import [public](../../../csharp/language-reference/keywords/public.md) type information in the specified file into the current project, thus enabling you to reference metadata from the specified assembly files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec593-104">語法</span><span class="sxs-lookup"><span data-stu-id="ec593-104">Syntax</span></span>  
  
```console  
-reference:[alias=]filename  
-reference:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="ec593-105">引數</span><span class="sxs-lookup"><span data-stu-id="ec593-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="ec593-106">含有組件資訊清單 (Assembly Manifest) 的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="ec593-106">The name of a file that contains an assembly manifest.</span></span> <span data-ttu-id="ec593-107">若要匯入多個檔案，請為每個檔案納入個別的 **-reference** 選項。</span><span class="sxs-lookup"><span data-stu-id="ec593-107">To import more than one file, include a separate **-reference** option for each file.</span></span>  
  
 `alias`  
 <span data-ttu-id="ec593-108">有效的 C# 識別項，代表包含組件中所有命名空間的根命名空間。</span><span class="sxs-lookup"><span data-stu-id="ec593-108">A valid C# identifier that will represent a root namespace that will contain all namespaces in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec593-109">備註</span><span class="sxs-lookup"><span data-stu-id="ec593-109">Remarks</span></span>  
 <span data-ttu-id="ec593-110">若要從多個檔案進行匯入，請為每個檔案納入 **-reference** 選項。</span><span class="sxs-lookup"><span data-stu-id="ec593-110">To import from more than one file, include a **-reference** option for each file.</span></span>  
  
 <span data-ttu-id="ec593-111">您匯入的檔案必須包含資訊清單，且輸出檔案必須已使用其中一個 [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) 選項進行編譯 ([-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) 除外)。</span><span class="sxs-lookup"><span data-stu-id="ec593-111">The files you import must contain a manifest; the output file must have been compiled with one of the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) options other than [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).</span></span>  
  
 <span data-ttu-id="ec593-112">**-r** 是 **-reference** 的簡短形式。</span><span class="sxs-lookup"><span data-stu-id="ec593-112">**-r** is the short form of **-reference**.</span></span>  
  
 <span data-ttu-id="ec593-113">如果輸出檔案不包含組件資訊清單，請使用 [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) 以從中匯入中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ec593-113">Use [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) to import metadata from an output file that does not contain an assembly manifest.</span></span>  
  
 <span data-ttu-id="ec593-114">如果您參考的組件 (組件 A) 有參考其他組件 (組件 B)，則在下列情況中，您也需要參考 B 組件：</span><span class="sxs-lookup"><span data-stu-id="ec593-114">If you reference an assembly (Assembly A) that references another assembly (Assembly B), you will need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="ec593-115">您使用的類型是來自組件 A，但繼承自組件 B 的類型，或是實作組件 B 的介面。</span><span class="sxs-lookup"><span data-stu-id="ec593-115">A type you use from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="ec593-116">您所叫用的欄位、屬性、事件或方法具有組件 B 的傳回型別或參數類型。</span><span class="sxs-lookup"><span data-stu-id="ec593-116">You invoke a field, property, event, or method that has a return type or parameter type from Assembly B.</span></span>  
  
 <span data-ttu-id="ec593-117">使用 [-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md)，以指定一或多個組件參考所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="ec593-117">Use [-lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md) to specify the directory in which one or more of your assembly references is located.</span></span> <span data-ttu-id="ec593-118">**-lib** 主題也會說明編譯器會在其中搜尋組件的目錄。</span><span class="sxs-lookup"><span data-stu-id="ec593-118">The **-lib** topic also discusses the directories in which the compiler searches for assemblies.</span></span>  
  
 <span data-ttu-id="ec593-119">為了讓編譯器可以辨識位於組件中的類型 (而不是模組中)，您必須定義類型的執行個體，以強制讓編譯器解析類型。</span><span class="sxs-lookup"><span data-stu-id="ec593-119">In order for the compiler to recognize a type in an assembly, and not in a module, it needs to be forced to resolve the type, which you can do by defining an instance of the type.</span></span> <span data-ttu-id="ec593-120">您也可以使用其他方法，讓編譯器解析組件中的類型名稱：例如，您可以繼承組件的類型，編譯器即可辨識類型名稱。</span><span class="sxs-lookup"><span data-stu-id="ec593-120">There are other ways to resolve type names in an assembly for the compiler: for example, if you inherit from a type in an assembly, the type name will then be recognized by the compiler.</span></span>  
  
 <span data-ttu-id="ec593-121">有時候，您必須參考組件內相同元件的兩個不同版本。</span><span class="sxs-lookup"><span data-stu-id="ec593-121">Sometimes it is necessary to reference two different versions of the same component from within one assembly.</span></span> <span data-ttu-id="ec593-122">若要這樣做，請針對每個檔案，使用 **-reference** 參數上的別名子選項，以區別兩個不同的檔案。</span><span class="sxs-lookup"><span data-stu-id="ec593-122">To do this, use the alias suboption on the **-reference** switch for each file to distinguish between the two files.</span></span> <span data-ttu-id="ec593-123">系統會將此別名作為元件名稱的限定詞，並將元件解析為其中一個檔案。</span><span class="sxs-lookup"><span data-stu-id="ec593-123">This alias will be used as a qualifier for the component name, and will resolve to the component in one of the files.</span></span>  
  
 <span data-ttu-id="ec593-124">預設會使用 csc 回應檔 (.rsp)，以參考常用的 .NET Framework 組件。</span><span class="sxs-lookup"><span data-stu-id="ec593-124">The csc response (.rsp) file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="ec593-125">如果您不想讓編譯器使用 csc.rsp，可使用 [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="ec593-125">Use [-noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) if you do not want the compiler to use csc.rsp.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec593-126">在 Visual Studio 中，使用 [新增參考] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ec593-126">In Visual Studio, use the **Add Reference** dialog box.</span></span> <span data-ttu-id="ec593-127">如需詳細資訊，請參閱[如何：使用參考管理員新增或移除參考](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)。</span><span class="sxs-lookup"><span data-stu-id="ec593-127">For more information, see [How to: Add or Remove References By Using the Reference Manager](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).</span></span> <span data-ttu-id="ec593-128">新增參考時，為了確保使用 `-reference` 以及使用 [新增參考] 對話方塊的對等行為，請將您要新增之組件的 [內嵌 Interop 類型] 屬性設為 **False**。</span><span class="sxs-lookup"><span data-stu-id="ec593-128">To ensure equivalent behavior between adding references by using `-reference` and adding references by using the **Add Reference** dialog box, set the **Embed Interop Types** property to **False** for the assembly that you're adding.</span></span> <span data-ttu-id="ec593-129">這個屬性的預設值為 **True**。</span><span class="sxs-lookup"><span data-stu-id="ec593-129">**True** is the default value for the property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec593-130">範例</span><span class="sxs-lookup"><span data-stu-id="ec593-130">Example</span></span>  
 <span data-ttu-id="ec593-131">這個範例會示範如何使用[外部別名](../../../csharp/language-reference/keywords/extern-alias.md)功能。</span><span class="sxs-lookup"><span data-stu-id="ec593-131">This example shows how to use the [extern alias](../../../csharp/language-reference/keywords/extern-alias.md) feature.</span></span>  
  
 <span data-ttu-id="ec593-132">您可以編譯原始檔，並從先前編譯過的 `grid.dll` 和 `grid20.dll` 匯入中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ec593-132">You compile the source file and import metadata from `grid.dll` and `grid20.dll`, which have been compiled previously.</span></span> <span data-ttu-id="ec593-133">這兩個 DLL 包含相同元件的不同版本，因此您需要搭配使用兩個 **-reference** 與別名選項，來編譯原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="ec593-133">The two DLLs contain separate versions of the same component, and you use two **-reference** with alias options to compile the source file.</span></span> <span data-ttu-id="ec593-134">選項應該看起來像這樣︰</span><span class="sxs-lookup"><span data-stu-id="ec593-134">The options look like this:</span></span>  

```console
-reference:GridV1=grid.dll -reference:GridV2=grid20.dll  
```
  
 <span data-ttu-id="ec593-135">這會設定 `GridV1` 和 `GridV2` 外部別名，您可透過 `extern` 陳述式以在程式中使用這些別名：</span><span class="sxs-lookup"><span data-stu-id="ec593-135">This sets up the external aliases `GridV1` and `GridV2`, which you use in your program by means of an `extern` statement:</span></span>  
  
```csharp  
extern alias GridV1;  
extern alias GridV2;  
// Using statements go here.  
```  
  
 <span data-ttu-id="ec593-136">完成之後，您可以在 `GridV1` 前面加上控制項名稱，以參照 `grid.dll` 的方格控制項，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ec593-136">Once this is done, you can refer to the grid control from `grid.dll` by prefixing the control name with `GridV1`, like this:</span></span>  
  
```csharp  
GridV1::Grid  
```  
  
 <span data-ttu-id="ec593-137">此外，您可以在 `GridV2` 前面加上控制項名稱，以參照 `grid20.dll` 的方格控制項，如下所示：</span><span class="sxs-lookup"><span data-stu-id="ec593-137">In addition, you can refer to the grid control from `grid20.dll` by prefixing the control name with `GridV2` like this:</span></span>  
  
```csharp  
GridV2::Grid   
```  
  
## <a name="see-also"></a><span data-ttu-id="ec593-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec593-138">See also</span></span>

- [<span data-ttu-id="ec593-139">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="ec593-139">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="ec593-140">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="ec593-140">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
