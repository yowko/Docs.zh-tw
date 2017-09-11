---
title: "-target (C# 編譯器選項) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /target
dev_langs:
- CSharp
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 615a0e2993dc78919008e8f9245504a486e2fb77
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="target-c-compiler-options"></a><span data-ttu-id="0a2e2-102">/target (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="0a2e2-102">/target (C# Compiler Options)</span></span>
<span data-ttu-id="0a2e2-103">您可以使用四種形式之一來指定**/target** 編譯器選項︰</span><span class="sxs-lookup"><span data-stu-id="0a2e2-103">The **/target** compiler option can be specified in one of four forms:</span></span>  
  
 [<span data-ttu-id="0a2e2-104">/target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="0a2e2-104">/target:appcontainerexe</span></span>](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="0a2e2-105">建立 [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)]應用程式的 .exe 檔。</span><span class="sxs-lookup"><span data-stu-id="0a2e2-105">To create an .exe file for [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)] apps.</span></span>  
  
 [<span data-ttu-id="0a2e2-106">/target:exe</span><span class="sxs-lookup"><span data-stu-id="0a2e2-106">/target:exe</span></span>](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 <span data-ttu-id="0a2e2-107">建立 .exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="0a2e2-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="0a2e2-108">/target:library</span><span class="sxs-lookup"><span data-stu-id="0a2e2-108">/target:library</span></span>](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 <span data-ttu-id="0a2e2-109">建立程式碼程式庫。</span><span class="sxs-lookup"><span data-stu-id="0a2e2-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="0a2e2-110">/target:module</span><span class="sxs-lookup"><span data-stu-id="0a2e2-110">/target:module</span></span>](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 <span data-ttu-id="0a2e2-111">建立模組。</span><span class="sxs-lookup"><span data-stu-id="0a2e2-111">To create a module.</span></span>  
  
 [<span data-ttu-id="0a2e2-112">/target:winexe</span><span class="sxs-lookup"><span data-stu-id="0a2e2-112">/target:winexe</span></span>](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 <span data-ttu-id="0a2e2-113">建立 Windows 程式。</span><span class="sxs-lookup"><span data-stu-id="0a2e2-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="0a2e2-114">/target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="0a2e2-114">/target:winmdobj</span></span>](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 <span data-ttu-id="0a2e2-115">建立中繼 .winmdobj 檔案。</span><span class="sxs-lookup"><span data-stu-id="0a2e2-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="0a2e2-116">除非您指定 **/target:module**，否則 **/target** 會將 .NET Framework 組件資訊清單放入輸出檔中。</span><span class="sxs-lookup"><span data-stu-id="0a2e2-116">Unless you specify **/target:module**, **/target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="0a2e2-117">如需詳細資訊，請參閱 [Common Language Runtime 中的組件](https://msdn.microsoft.com/library/k3677y81)和 [Common Attributes](http://msdn.microsoft.com/library/2f48a7ec-9683-4899-a1d2-a08be8fc558b) (常見屬性)。</span><span class="sxs-lookup"><span data-stu-id="0a2e2-117">For more information, see [Assemblies in the Common Language Runtime](https://msdn.microsoft.com/library/k3677y81) and [Common Attributes](http://msdn.microsoft.com/library/2f48a7ec-9683-4899-a1d2-a08be8fc558b).</span></span>  
  
 <span data-ttu-id="0a2e2-118">編譯時，組件資訊清單會放在第一個 .exe 輸出檔，如果沒有 .exe 輸出檔，則會放在第一個 DLL 中。</span><span class="sxs-lookup"><span data-stu-id="0a2e2-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="0a2e2-119">例如，在下列命令列中，資訊清單會放在 `1.exe` 中：</span><span class="sxs-lookup"><span data-stu-id="0a2e2-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```  
csc /out:1.exe t1.cs /out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="0a2e2-120">編譯器在每次編譯時都只會建立一個組件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="0a2e2-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="0a2e2-121">編譯中所有檔案的資訊會放入組件資訊清單中。</span><span class="sxs-lookup"><span data-stu-id="0a2e2-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="0a2e2-122">使用 **/target:module** 所建立的輸出檔以外的所有輸出檔都可以包含組件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="0a2e2-122">All output files except those created with **/target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="0a2e2-123">在命令列產生多個輸出檔時，只能建立一個組件資訊清單，而且它必須移至命令列上所指定的第一個輸出檔。</span><span class="sxs-lookup"><span data-stu-id="0a2e2-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="0a2e2-124">不論第一個輸出檔為 (**/target:exe**、**/target:winexe**、**/target:library** 還是 **/target:module**)，在相同編譯中產生的任何其他輸出檔都必須是模組 (**/target:module**)。</span><span class="sxs-lookup"><span data-stu-id="0a2e2-124">No matter what the first output file is (**/target:exe**, **/target:winexe**, **/target:library** or **/target:module**), any other output files produced in the same compilation must be modules (**/target:module**).</span></span>  
  
 <span data-ttu-id="0a2e2-125">如果您建立組件，則可以使用 <xref:System.CLSCompliantAttribute> 屬性指出所有或部分程式碼符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="0a2e2-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="0a2e2-126">如需如何以程式設計方式設定此編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。</span><span class="sxs-lookup"><span data-stu-id="0a2e2-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a2e2-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a2e2-127">See Also</span></span>  
 <span data-ttu-id="0a2e2-128">[C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="0a2e2-128">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
<span data-ttu-id="0a2e2-129"> [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span><span class="sxs-lookup"><span data-stu-id="0a2e2-129"> [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span></span>  
<span data-ttu-id="0a2e2-130"> [/subsystemversion (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="0a2e2-130"> [/subsystemversion (C# Compiler Options)](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)</span></span>
