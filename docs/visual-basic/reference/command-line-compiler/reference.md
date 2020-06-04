---
title: -reference
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: 633b457106203e213f5d30003e576b7e8132f4d2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400483"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="88e5d-102">-reference （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="88e5d-102">-reference (Visual Basic)</span></span>
<span data-ttu-id="88e5d-103">讓編譯器將指定元件中的類型資訊提供給您目前編譯的專案。</span><span class="sxs-lookup"><span data-stu-id="88e5d-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88e5d-104">語法</span><span class="sxs-lookup"><span data-stu-id="88e5d-104">Syntax</span></span>  
  
```console  
-reference:fileList  
```

<span data-ttu-id="88e5d-105">或</span><span class="sxs-lookup"><span data-stu-id="88e5d-105">or</span></span>

```console
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="88e5d-106">引數</span><span class="sxs-lookup"><span data-stu-id="88e5d-106">Arguments</span></span>  
  
|<span data-ttu-id="88e5d-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="88e5d-107">Term</span></span>|<span data-ttu-id="88e5d-108">定義</span><span class="sxs-lookup"><span data-stu-id="88e5d-108">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="88e5d-109">必要。</span><span class="sxs-lookup"><span data-stu-id="88e5d-109">Required.</span></span> <span data-ttu-id="88e5d-110">以逗號分隔的組件檔案名稱清單。</span><span class="sxs-lookup"><span data-stu-id="88e5d-110">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="88e5d-111">如果檔案名稱包含空格，請用引號括住名稱。</span><span class="sxs-lookup"><span data-stu-id="88e5d-111">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88e5d-112">備註</span><span class="sxs-lookup"><span data-stu-id="88e5d-112">Remarks</span></span>  
 <span data-ttu-id="88e5d-113">您匯入的檔案必須包含元件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="88e5d-113">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="88e5d-114">只有公用類型才會顯示在元件外部。</span><span class="sxs-lookup"><span data-stu-id="88e5d-114">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="88e5d-115">[-Addmodule](addmodule.md)選項會從模組匯入中繼資料。</span><span class="sxs-lookup"><span data-stu-id="88e5d-115">The [-addmodule](addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="88e5d-116">如果您參考的元件（元件 A）本身參考另一個元件（元件 B），則在下列情況中，您必須參考元件 B：</span><span class="sxs-lookup"><span data-stu-id="88e5d-116">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="88e5d-117">組件 A 的類型繼承自組件 B 的類型，或是實作組件 B 的介面。</span><span class="sxs-lookup"><span data-stu-id="88e5d-117">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="88e5d-118">所叫用的欄位、屬性、事件或方法具有組件 B 的傳回型別或參數類型。</span><span class="sxs-lookup"><span data-stu-id="88e5d-118">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="88e5d-119">請使用[-libpath](libpath.md)來指定您的一或多個元件參考所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="88e5d-119">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="88e5d-120">為了讓編譯器辨識元件中的型別（而不是模組），必須強制解析型別。</span><span class="sxs-lookup"><span data-stu-id="88e5d-120">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="88e5d-121">如何執行這項操作的其中一個範例是定義類型的實例。</span><span class="sxs-lookup"><span data-stu-id="88e5d-121">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="88e5d-122">其他方式可用來解析編譯器元件中的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="88e5d-122">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="88e5d-123">例如，如果您繼承自元件中的類型，則編譯器會知道該類型名稱。</span><span class="sxs-lookup"><span data-stu-id="88e5d-123">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="88e5d-124">預設會使用用來參考常用 .NET Framework 元件的 Vbc 回應檔。</span><span class="sxs-lookup"><span data-stu-id="88e5d-124">The Vbc.rsp response file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="88e5d-125">`-noconfig`如果您不想讓編譯器使用 Vbc，請使用。</span><span class="sxs-lookup"><span data-stu-id="88e5d-125">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="88e5d-126">`-reference` 的簡短形式為 `-r`。</span><span class="sxs-lookup"><span data-stu-id="88e5d-126">The short form of `-reference` is `-r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88e5d-127">範例</span><span class="sxs-lookup"><span data-stu-id="88e5d-127">Example</span></span>  
 <span data-ttu-id="88e5d-128">下列命令會從編譯原始 `Input.vb` 程式檔和參考元件，並 `Metad1.dll` `Metad2.dll` 產生 `Out.exe` 。</span><span class="sxs-lookup"><span data-stu-id="88e5d-128">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="88e5d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88e5d-129">See also</span></span>

- [<span data-ttu-id="88e5d-130">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="88e5d-130">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="88e5d-131">-noconfig</span><span class="sxs-lookup"><span data-stu-id="88e5d-131">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="88e5d-132">-target （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="88e5d-132">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="88e5d-133">公開</span><span class="sxs-lookup"><span data-stu-id="88e5d-133">Public</span></span>](../../language-reference/modifiers/public.md)
- [<span data-ttu-id="88e5d-134">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="88e5d-134">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
