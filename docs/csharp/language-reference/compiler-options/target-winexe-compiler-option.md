---
title: -target:winexe (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 5d5e5c62dc1a5fe6901ee232084a704d7d936b76
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411959"
---
# <a name="-targetwinexe-c-compiler-options"></a><span data-ttu-id="ad7d6-102">-target:winexe (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="ad7d6-102">-target:winexe (C# Compiler Options)</span></span>
<span data-ttu-id="ad7d6-103">**-target:winexe** 選項可讓編譯器建立可執行檔 (EXE)，其為一個 Windows 程式。</span><span class="sxs-lookup"><span data-stu-id="ad7d6-103">The **-target:winexe** option causes the compiler to create an executable (EXE), Windows program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad7d6-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad7d6-104">Syntax</span></span>  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a><span data-ttu-id="ad7d6-105">備註</span><span class="sxs-lookup"><span data-stu-id="ad7d6-105">Remarks</span></span>  
 <span data-ttu-id="ad7d6-106">將會建立副檔名為 .exe 的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="ad7d6-106">The executable file will be created with the .exe extension.</span></span> <span data-ttu-id="ad7d6-107">Windows 程式是從 .NET Framework 程式庫或使用 Windows API 提供使用者介面的程式。</span><span class="sxs-lookup"><span data-stu-id="ad7d6-107">A Windows program is one that provides a user interface from either the .NET Framework library or with the Windows APIs.</span></span>  
  
 <span data-ttu-id="ad7d6-108">使用 [-target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) 建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="ad7d6-108">Use [-target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) to create a console application.</span></span>  
  
 <span data-ttu-id="ad7d6-109">除非特別使用 [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) 選項指定輸出檔案名稱，否則輸出檔案名稱會採用包含 [Main](../../../csharp/programming-guide/main-and-command-args/index.md) 方法的輸入檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="ad7d6-109">Unless otherwise specified with the [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="ad7d6-110">指定於命令列時，下一個 **-out** 或 [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) 選項之前的所有檔案都是用來建立 Windows 程式。</span><span class="sxs-lookup"><span data-stu-id="ad7d6-110">When specified at the command line, all files until the next **-out** or [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) option are used to create the Windows program.</span></span>  
  
 <span data-ttu-id="ad7d6-111">編譯為 .exe 檔案的原始程式碼檔中只需要一個 **Main** 方法。</span><span class="sxs-lookup"><span data-stu-id="ad7d6-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="ad7d6-112">如果您的程式碼有多個具有 **Main** 方法的類別，則 [-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) 選項可讓您指定哪個類別包含 **Main** 方法。</span><span class="sxs-lookup"><span data-stu-id="ad7d6-112">The [-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ad7d6-113">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="ad7d6-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="ad7d6-114">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="ad7d6-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="ad7d6-115">按一下 [應用程式] 屬性頁。</span><span class="sxs-lookup"><span data-stu-id="ad7d6-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="ad7d6-116">修改 [輸出類型] 屬性。</span><span class="sxs-lookup"><span data-stu-id="ad7d6-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="ad7d6-117">如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。</span><span class="sxs-lookup"><span data-stu-id="ad7d6-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad7d6-118">範例</span><span class="sxs-lookup"><span data-stu-id="ad7d6-118">Example</span></span>  
 <span data-ttu-id="ad7d6-119">將 `in.cs` 編譯為 Windows 程式︰</span><span class="sxs-lookup"><span data-stu-id="ad7d6-119">Compile `in.cs` into a Windows program:</span></span>  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="ad7d6-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad7d6-120">See also</span></span>

- [<span data-ttu-id="ad7d6-121">-target (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="ad7d6-121">-target (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [<span data-ttu-id="ad7d6-122">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="ad7d6-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
