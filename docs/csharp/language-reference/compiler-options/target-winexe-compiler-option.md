---
title: "-target:winexe (C# 編譯器選項) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /target:winexe
dev_langs:
- CSharp
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
caps.latest.revision: 11
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
ms.sourcegitcommit: bb28bf28c3d8a426322e1c1795941de7e9aa4bf6
ms.openlocfilehash: 053f9299a83a8d4796a20363a699e9d81a427828
ms.contentlocale: zh-tw
ms.lasthandoff: 05/31/2017

---
# <a name="targetwinexe-c-compiler-options"></a><span data-ttu-id="44573-102">/target:winexe (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="44573-102">/target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="44573-103">**/target:winexe** 選項可讓編譯器建立可執行檔 (EXE)，其為一個 Windows 程式。</span><span class="sxs-lookup"><span data-stu-id="44573-103">The **/target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44573-104">語法</span><span class="sxs-lookup"><span data-stu-id="44573-104">Syntax</span></span>  
  
```console  
/target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="44573-105">備註</span><span class="sxs-lookup"><span data-stu-id="44573-105">Remarks</span></span>  
 <span data-ttu-id="44573-106">將會建立副檔名為 .exe 的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="44573-106">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="44573-107">Windows 程式是從 .NET Framework 程式庫或使用 Win32 API 提供使用者介面的程式。</span><span class="sxs-lookup"><span data-stu-id="44573-107">A Windows program is one that provides a user interface from either the .NET Framework library or with the Win32 APIs.</span></span>  
  
 <span data-ttu-id="44573-108">使用 [/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) 建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="44573-108">Use [/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="44573-109">除非特別使用 [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) 選項指定輸出檔名稱，否則輸出檔名稱會採用包含 [Main](../../../csharp/programming-guide/main-and-command-args/index.md) 方法的輸入檔名稱。</span><span class="sxs-lookup"><span data-stu-id="44573-109">Unless otherwise specified with the [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="44573-110">指定於命令列時，下一個 **/out** 或 [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) 選項之前的所有檔案都是用來建立 Windows 程式。</span><span class="sxs-lookup"><span data-stu-id="44573-110">When specified at the command line, all files until the next **/out** or [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="44573-111">編譯為 .exe 檔案的原始程式碼檔中只需要一個 **Main** 方法。</span><span class="sxs-lookup"><span data-stu-id="44573-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="44573-112">如果您的程式碼有多個具有 **Main** 方法的類別，則 [/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) 選項可讓您指定哪個類別包含 **Main** 方法。</span><span class="sxs-lookup"><span data-stu-id="44573-112">The [/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="44573-113">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="44573-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="44573-114">開啟專案的 [屬性]**** 頁面。</span><span class="sxs-lookup"><span data-stu-id="44573-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="44573-115">按一下 [應用程式]**** 屬性頁。</span><span class="sxs-lookup"><span data-stu-id="44573-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="44573-116">修改 [輸出類型]**** 屬性。</span><span class="sxs-lookup"><span data-stu-id="44573-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="44573-117">如需如何以程式設計方式設定此編譯器選項的資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。</span><span class="sxs-lookup"><span data-stu-id="44573-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44573-118">範例</span><span class="sxs-lookup"><span data-stu-id="44573-118">Example</span></span>  
 <span data-ttu-id="44573-119">將 `in.cs` 編譯為 Windows 程式︰</span><span class="sxs-lookup"><span data-stu-id="44573-119">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc /target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="44573-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44573-120">See Also</span></span>  
 <span data-ttu-id="44573-121">[/target (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/target-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="44573-121">[/target (C# Compiler Options)](../../../csharp/language-reference/compiler-options/target-compiler-option.md) </span></span>  
<span data-ttu-id="44573-122"> [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)</span><span class="sxs-lookup"><span data-stu-id="44573-122"> [C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)</span></span>
