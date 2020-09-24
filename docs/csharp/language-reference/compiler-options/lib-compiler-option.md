---
description: -lib (C# 編譯器選項)
title: -lib (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
ms.openlocfilehash: 9478501ea98ec1b9d3ec2761bc4ebf3f6bef656c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152438"
---
# <a name="-lib-c-compiler-options"></a><span data-ttu-id="d1e30-103">-lib (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="d1e30-103">-lib (C# Compiler Options)</span></span>

<span data-ttu-id="d1e30-104">**-Lib**選項會指定由[-Reference (c # 編譯器選項) ](./reference-compiler-option.md)選項參考之元件的位置。</span><span class="sxs-lookup"><span data-stu-id="d1e30-104">The **-lib** option specifies the location of assemblies referenced by means of the [-reference (C# Compiler Options)](./reference-compiler-option.md) option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1e30-105">語法</span><span class="sxs-lookup"><span data-stu-id="d1e30-105">Syntax</span></span>  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d1e30-106">引數</span><span class="sxs-lookup"><span data-stu-id="d1e30-106">Arguments</span></span>  

 `dir1`  
 <span data-ttu-id="d1e30-107">如果編譯器在目前的工作目錄 (您叫用編譯器的起點目錄) 或通用語言執行平台的系統目錄中找不到參考的組件，會改為查詢的目錄。</span><span class="sxs-lookup"><span data-stu-id="d1e30-107">A directory for the compiler to look in if a referenced assembly is not found in the current working directory (the directory from which you are invoking the compiler) or in the common language runtime's system directory.</span></span>  
  
 `dir2`  
 <span data-ttu-id="d1e30-108">用來尋找組件參考的一或多個其他目錄。</span><span class="sxs-lookup"><span data-stu-id="d1e30-108">One or more additional directories to search in for assembly references.</span></span> <span data-ttu-id="d1e30-109">使用逗號分隔額外的目錄名稱；之間不含任何空白字元。</span><span class="sxs-lookup"><span data-stu-id="d1e30-109">Separate additional directory names with a comma, and without white space between them.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1e30-110">備註</span><span class="sxs-lookup"><span data-stu-id="d1e30-110">Remarks</span></span>  

 <span data-ttu-id="d1e30-111">編譯器會以下列順序搜尋不完整的組件參考：</span><span class="sxs-lookup"><span data-stu-id="d1e30-111">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="d1e30-112">目前的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="d1e30-112">Current working directory.</span></span> <span data-ttu-id="d1e30-113">這是叫用編譯器的起點目錄。</span><span class="sxs-lookup"><span data-stu-id="d1e30-113">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="d1e30-114">通用語言執行平台系統目錄。</span><span class="sxs-lookup"><span data-stu-id="d1e30-114">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="d1e30-115">**-lib** 所指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="d1e30-115">Directories specified by **-lib**.</span></span>  
  
4. <span data-ttu-id="d1e30-116">LIB 環境變數所指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="d1e30-116">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="d1e30-117">使用 **-reference** 來指定組件參考。</span><span class="sxs-lookup"><span data-stu-id="d1e30-117">Use **-reference** to specify an assembly reference.</span></span>  
  
 <span data-ttu-id="d1e30-118">**-lib** 為加法；指定超過一次時，即會附加到任何先前的值。</span><span class="sxs-lookup"><span data-stu-id="d1e30-118">**-lib** is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="d1e30-119">若不想使用 **-lib**，替代方法是將任何必要的組件複製到工作目錄中；這樣一來，您就只需將組件名稱傳遞給 **-reference**。</span><span class="sxs-lookup"><span data-stu-id="d1e30-119">An alternative to using **-lib** is to copy into the working directory any required assemblies; this will allow you to simply pass the assembly name to **-reference**.</span></span> <span data-ttu-id="d1e30-120">接著，您就可以從工作目錄刪除組件。</span><span class="sxs-lookup"><span data-stu-id="d1e30-120">You can then delete the assemblies from the working directory.</span></span> <span data-ttu-id="d1e30-121">由於資訊清單中未指定相依組件的路徑，因此應用程式可以在目標電腦上啟動，並在全域組件快取中尋找和使用組件。</span><span class="sxs-lookup"><span data-stu-id="d1e30-121">Since the path to the dependent assembly is not specified in the assembly manifest, the application can be started on the target computer and will find and use the assembly in the global assembly cache.</span></span>  
  
 <span data-ttu-id="d1e30-122">即使編譯器可以參考組件，也不表示通用語言執行平台都能夠在執行階段尋找和載入組件。</span><span class="sxs-lookup"><span data-stu-id="d1e30-122">Because the compiler can reference the assembly does not imply the common language runtime will be able to find and load the assembly at runtime.</span></span> <span data-ttu-id="d1e30-123">如需執行階段如何搜尋參考組件的詳細資訊，請參閱[執行階段如何找出組件](../../../framework/deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="d1e30-123">See [How the Runtime Locates Assemblies](../../../framework/deployment/how-the-runtime-locates-assemblies.md) for details on how the runtime searches for referenced assemblies.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d1e30-124">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="d1e30-124">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="d1e30-125">開啟專案的 [屬性頁] \*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d1e30-125">Open the project's **Property Pages** dialog box.</span></span>  
  
2. <span data-ttu-id="d1e30-126">按一下 [參考路徑]\*\*\*\* 屬性頁。</span><span class="sxs-lookup"><span data-stu-id="d1e30-126">Click the **References Path** property page.</span></span>  
  
3. <span data-ttu-id="d1e30-127">修改清單方塊的內容。</span><span class="sxs-lookup"><span data-stu-id="d1e30-127">Modify the contents of the list box.</span></span>  
  
 <span data-ttu-id="d1e30-128">如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>。</span><span class="sxs-lookup"><span data-stu-id="d1e30-128">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1e30-129">範例</span><span class="sxs-lookup"><span data-stu-id="d1e30-129">Example</span></span>  

 <span data-ttu-id="d1e30-130">編譯 t2.cs 以建立 .exe 檔。</span><span class="sxs-lookup"><span data-stu-id="d1e30-130">Compile t2.cs to create an .exe file.</span></span> <span data-ttu-id="d1e30-131">編譯器會在工作目錄和 C 磁碟機的根目錄中尋找組件參考。</span><span class="sxs-lookup"><span data-stu-id="d1e30-131">The compiler will look in the working directory and in the root directory of the C drive for assembly references.</span></span>  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1e30-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1e30-132">See also</span></span>

- [<span data-ttu-id="d1e30-133">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="d1e30-133">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="d1e30-134">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="d1e30-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
