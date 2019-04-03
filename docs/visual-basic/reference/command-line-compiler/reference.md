---
title: -參考 (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: 21efca701eb16898dd291d73bf0431641ba75d12
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826115"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="56ee2-102">-參考 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56ee2-102">-reference (Visual Basic)</span></span>
<span data-ttu-id="56ee2-103">可讓編譯器進行指定的組件中的類型資訊提供給您目前編譯的專案。</span><span class="sxs-lookup"><span data-stu-id="56ee2-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56ee2-104">語法</span><span class="sxs-lookup"><span data-stu-id="56ee2-104">Syntax</span></span>  
  
```  
-reference:fileList  
' -or-  
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="56ee2-105">引數</span><span class="sxs-lookup"><span data-stu-id="56ee2-105">Arguments</span></span>  
  
|<span data-ttu-id="56ee2-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="56ee2-106">Term</span></span>|<span data-ttu-id="56ee2-107">定義</span><span class="sxs-lookup"><span data-stu-id="56ee2-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="56ee2-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="56ee2-108">Required.</span></span> <span data-ttu-id="56ee2-109">以逗號分隔的組件檔案名稱清單。</span><span class="sxs-lookup"><span data-stu-id="56ee2-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="56ee2-110">如果檔案名稱包含空格，請用引號括住名稱。</span><span class="sxs-lookup"><span data-stu-id="56ee2-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56ee2-111">備註</span><span class="sxs-lookup"><span data-stu-id="56ee2-111">Remarks</span></span>  
 <span data-ttu-id="56ee2-112">您匯入的檔案必須包含組件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="56ee2-112">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="56ee2-113">只有公用型別是組件外部可見的。</span><span class="sxs-lookup"><span data-stu-id="56ee2-113">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="56ee2-114">[/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)選項，從模組匯入中繼資料。</span><span class="sxs-lookup"><span data-stu-id="56ee2-114">The [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="56ee2-115">如果您參考的組件 （組件 A） 本身參考另一個組件 (組件 B)，如果您需要參考 B 組件：</span><span class="sxs-lookup"><span data-stu-id="56ee2-115">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
-   <span data-ttu-id="56ee2-116">組件 A 的類型繼承自組件 B 的類型，或是實作組件 B 的介面。</span><span class="sxs-lookup"><span data-stu-id="56ee2-116">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="56ee2-117">所叫用的欄位、屬性、事件或方法具有組件 B 的傳回型別或參數類型。</span><span class="sxs-lookup"><span data-stu-id="56ee2-117">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="56ee2-118">使用[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)指定一或多個組件參考所在的目錄。</span><span class="sxs-lookup"><span data-stu-id="56ee2-118">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="56ee2-119">編譯器無法辨識的組件 （而非模組） 中的型別，它必須強制執行解析的型別。</span><span class="sxs-lookup"><span data-stu-id="56ee2-119">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="56ee2-120">執行這其中一個範例是定義類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="56ee2-120">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="56ee2-121">其他方式可解決編譯器的組件中的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="56ee2-121">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="56ee2-122">比方說，如果您繼承自組件中的類型，類型名稱就會知道給編譯器。</span><span class="sxs-lookup"><span data-stu-id="56ee2-122">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="56ee2-123">參考常用的 Vbc.rsp 回應檔[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]組件，預設會使用。</span><span class="sxs-lookup"><span data-stu-id="56ee2-123">The Vbc.rsp response file, which references commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies, is used by default.</span></span> <span data-ttu-id="56ee2-124">使用`-noconfig`若不想讓編譯器使用 Vbc.rsp。</span><span class="sxs-lookup"><span data-stu-id="56ee2-124">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="56ee2-125">`-reference` 的簡短形式為 `/r`。</span><span class="sxs-lookup"><span data-stu-id="56ee2-125">The short form of `-reference` is `/r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56ee2-126">範例</span><span class="sxs-lookup"><span data-stu-id="56ee2-126">Example</span></span>  
 <span data-ttu-id="56ee2-127">下列命令會編譯原始程式檔`Input.vb`，並參考來自組件`Metad1.dll`並`Metad2.dll`產生`Out.exe`。</span><span class="sxs-lookup"><span data-stu-id="56ee2-127">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="56ee2-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56ee2-128">See also</span></span>

- [<span data-ttu-id="56ee2-129">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="56ee2-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="56ee2-130">-noconfig</span><span class="sxs-lookup"><span data-stu-id="56ee2-130">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="56ee2-131">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56ee2-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="56ee2-132">Public</span><span class="sxs-lookup"><span data-stu-id="56ee2-132">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="56ee2-133">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="56ee2-133">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
