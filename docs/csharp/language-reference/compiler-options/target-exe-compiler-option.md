---
title: "-target:exe (C# 編譯器選項) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /exe
dev_langs:
- CSharp
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
caps.latest.revision: 12
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
ms.openlocfilehash: 74d392781bf04b559c56ec74b093d120e416c147
ms.contentlocale: zh-tw
ms.lasthandoff: 05/31/2017

---
# <a name="targetexe-c-compiler-options"></a><span data-ttu-id="1116e-102">/target:exe (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="1116e-102">/target:exe (C# Compiler Options)</span></span>
<span data-ttu-id="1116e-103">**/target:exe** 選項可讓編譯器建立可執行檔 (EXE)：主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="1116e-103">The **/target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1116e-104">語法</span><span class="sxs-lookup"><span data-stu-id="1116e-104">Syntax</span></span>  
  
```console  
/target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="1116e-105">備註</span><span class="sxs-lookup"><span data-stu-id="1116e-105">Remarks</span></span>  
 <span data-ttu-id="1116e-106">**/target:exe** 選項預設為啟用。</span><span class="sxs-lookup"><span data-stu-id="1116e-106">The **/target:exe** option is in effect by default.</span></span> <span data-ttu-id="1116e-107">將會建立副檔名為 .exe 的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="1116e-107">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="1116e-108">使用 [/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) 建立 Windows 程式可執行檔。</span><span class="sxs-lookup"><span data-stu-id="1116e-108">Use [/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="1116e-109">除非特別使用 [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) 選項指定輸出檔名稱，否則輸出檔名稱會採用包含 [Main](../../../csharp/programming-guide/main-and-command-args/index.md) 方法的輸入檔名稱。</span><span class="sxs-lookup"><span data-stu-id="1116e-109">Unless otherwise specified with the [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="1116e-110">指定於命令列時，下一個 **/out** 或 **/target:module** 選項之前的所有檔案都是用來建立 .exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="1116e-110">When specified at the command line, all files up to the next **/out** or **/target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="1116e-111">編譯為 .exe 檔案的原始程式碼檔中只需要一個 **Main** 方法。</span><span class="sxs-lookup"><span data-stu-id="1116e-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="1116e-112">如果您的程式碼有多個具有 **Main** 方法的類別，則 [/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) 編譯器選項可讓您指定哪個類別包含 **Main** 方法。</span><span class="sxs-lookup"><span data-stu-id="1116e-112">The [/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1116e-113">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="1116e-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="1116e-114">開啟專案的 [屬性]**** 頁面。</span><span class="sxs-lookup"><span data-stu-id="1116e-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="1116e-115">按一下 [應用程式]**** 屬性頁。</span><span class="sxs-lookup"><span data-stu-id="1116e-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="1116e-116">修改 [輸出類型]**** 屬性。</span><span class="sxs-lookup"><span data-stu-id="1116e-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="1116e-117">如需如何以程式設計方式設定此編譯器選項的資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。</span><span class="sxs-lookup"><span data-stu-id="1116e-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1116e-118">範例</span><span class="sxs-lookup"><span data-stu-id="1116e-118">Example</span></span>  
 <span data-ttu-id="1116e-119">下列每個命令列都會建立 `in.exe` 來編譯 `in.cs`：</span><span class="sxs-lookup"><span data-stu-id="1116e-119">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc /target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="1116e-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1116e-120">See Also</span></span>  
 <span data-ttu-id="1116e-121">[/target (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/target-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="1116e-121">[/target (C# Compiler Options)](../../../csharp/language-reference/compiler-options/target-compiler-option.md) </span></span>  
<span data-ttu-id="1116e-122"> [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)</span><span class="sxs-lookup"><span data-stu-id="1116e-122"> [C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)</span></span>
