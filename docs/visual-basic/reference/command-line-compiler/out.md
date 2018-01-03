---
title: /out (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 53b77dec53be1d97c5f2526cb117933a2b8fe046
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="out-visual-basic"></a><span data-ttu-id="9c3b4-102">/out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c3b4-102">/out (Visual Basic)</span></span>
<span data-ttu-id="9c3b4-103">指定輸出檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c3b4-104">語法</span><span class="sxs-lookup"><span data-stu-id="9c3b4-104">Syntax</span></span>  
  
```  
/out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="9c3b4-105">引數</span><span class="sxs-lookup"><span data-stu-id="9c3b4-105">Arguments</span></span>  
  
|<span data-ttu-id="9c3b4-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="9c3b4-106">Term</span></span>|<span data-ttu-id="9c3b4-107">定義</span><span class="sxs-lookup"><span data-stu-id="9c3b4-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="9c3b4-108">必要。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-108">Required.</span></span> <span data-ttu-id="9c3b4-109">編譯器會建立輸出檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="9c3b4-110">如果檔案名稱包含空格，將名稱括在引號 ("")。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c3b4-111">備註</span><span class="sxs-lookup"><span data-stu-id="9c3b4-111">Remarks</span></span>  
 <span data-ttu-id="9c3b4-112">指定的完整名稱和要建立檔案的副檔名。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="9c3b4-113">如果不這麼做，.exe 檔會從原始程式檔包含其名稱`Sub Main`程序和.dll 檔案會從第一個原始程式檔取得其名稱。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="9c3b4-114">如果您指定檔案名稱沒有.exe 或.dll 副檔名，編譯器會自動延伸模組會為您加入，根據指定的值`/target`編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `/target` compiler option.</span></span>  
  
|<span data-ttu-id="9c3b4-115">若要在 Visual Studio 整合式的開發環境中的 out/設定</span><span class="sxs-lookup"><span data-stu-id="9c3b4-115">To set /out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="9c3b4-116">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9c3b4-117">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="9c3b4-118">2.按一下 [應用程式]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="9c3b4-119">3.修改中的值**組件名稱**方塊。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9c3b4-120">範例</span><span class="sxs-lookup"><span data-stu-id="9c3b4-120">Example</span></span>  
 <span data-ttu-id="9c3b4-121">下列程式碼編譯`T2.vb`並建立輸出檔`T2.exe`。</span><span class="sxs-lookup"><span data-stu-id="9c3b4-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```  
vbc t2.vb /out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c3b4-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="9c3b4-122">See Also</span></span>  
 [<span data-ttu-id="9c3b4-123">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="9c3b4-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="9c3b4-124">/target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c3b4-124">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="9c3b4-125">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="9c3b4-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
