---
description: -target:exe (C# 編譯器選項)
title: -target:exe (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: ae1706f1ecdd396e24711070d19420faa6d34761
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "91193755"
---
# <a name="-targetexe-c-compiler-options"></a><span data-ttu-id="60b07-103">-target:exe (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="60b07-103">-target:exe (C# Compiler Options)</span></span>

<span data-ttu-id="60b07-104">**-target:exe** 選項可讓編譯器建立可執行檔 (EXE)：主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="60b07-104">The **-target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60b07-105">語法</span><span class="sxs-lookup"><span data-stu-id="60b07-105">Syntax</span></span>  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="60b07-106">備註</span><span class="sxs-lookup"><span data-stu-id="60b07-106">Remarks</span></span>  

 <span data-ttu-id="60b07-107">**-target:exe** 選項預設為啟用。</span><span class="sxs-lookup"><span data-stu-id="60b07-107">The **-target:exe** option is in effect by default.</span></span> <span data-ttu-id="60b07-108">將會建立副檔名為 .exe 的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="60b07-108">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="60b07-109">使用 [-target:winexe](./target-winexe-compiler-option.md) 建立 Windows 程式可執行檔。</span><span class="sxs-lookup"><span data-stu-id="60b07-109">Use [-target:winexe](./target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="60b07-110">除非特別使用 [-out](./out-compiler-option.md) 選項指定輸出檔案名稱，否則輸出檔案名稱會採用包含 [Main](../../programming-guide/main-and-command-args/index.md) 方法的輸入檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="60b07-110">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="60b07-111">指定於命令列時，下一個 **-out** 或 **-target:module** 選項之前的所有檔案都是用來建立 .exe 檔案</span><span class="sxs-lookup"><span data-stu-id="60b07-111">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="60b07-112">編譯為 .exe 檔案的原始程式碼檔中只需要一個 **Main** 方法。</span><span class="sxs-lookup"><span data-stu-id="60b07-112">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="60b07-113">如果您的程式碼有多個具有 **Main** 方法的類別，則 [-main](./main-compiler-option.md) 編譯器選項可讓您指定哪個類別包含 **Main** 方法。</span><span class="sxs-lookup"><span data-stu-id="60b07-113">The [-main](./main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="60b07-114">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="60b07-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="60b07-115">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="60b07-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="60b07-116">按一下 [應用程式] 屬性頁。</span><span class="sxs-lookup"><span data-stu-id="60b07-116">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="60b07-117">修改 [輸出類型] 屬性。</span><span class="sxs-lookup"><span data-stu-id="60b07-117">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="60b07-118">如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。</span><span class="sxs-lookup"><span data-stu-id="60b07-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60b07-119">範例</span><span class="sxs-lookup"><span data-stu-id="60b07-119">Example</span></span>  

 <span data-ttu-id="60b07-120">下列每個命令列都會建立 `in.exe` 來編譯 `in.cs`：</span><span class="sxs-lookup"><span data-stu-id="60b07-120">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="60b07-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60b07-121">See also</span></span>

- [<span data-ttu-id="60b07-122">-目標 (c # 編譯器選項) </span><span class="sxs-lookup"><span data-stu-id="60b07-122">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="60b07-123">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="60b07-123">C# Compiler Options</span></span>](./index.md)
