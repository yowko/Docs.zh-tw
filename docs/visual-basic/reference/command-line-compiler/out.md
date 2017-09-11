---
title: "/out (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 489a9015718a581c793cd1217ba073625929daf3
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="out-visual-basic"></a><span data-ttu-id="9fba8-102">/out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fba8-102">/out (Visual Basic)</span></span>
<span data-ttu-id="9fba8-103">指定輸出檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="9fba8-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fba8-104">語法</span><span class="sxs-lookup"><span data-stu-id="9fba8-104">Syntax</span></span>  
  
```  
/out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="9fba8-105">引數</span><span class="sxs-lookup"><span data-stu-id="9fba8-105">Arguments</span></span>  
  
|<span data-ttu-id="9fba8-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="9fba8-106">Term</span></span>|<span data-ttu-id="9fba8-107">定義</span><span class="sxs-lookup"><span data-stu-id="9fba8-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="9fba8-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="9fba8-108">Required.</span></span> <span data-ttu-id="9fba8-109">編譯器會建立輸出檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="9fba8-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="9fba8-110">如果檔案名稱包含空格，將名稱括在引號 ("")。</span><span class="sxs-lookup"><span data-stu-id="9fba8-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fba8-111">備註</span><span class="sxs-lookup"><span data-stu-id="9fba8-111">Remarks</span></span>  
 <span data-ttu-id="9fba8-112">指定完整名稱和建立檔案的副檔名。</span><span class="sxs-lookup"><span data-stu-id="9fba8-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="9fba8-113">如果不這麼做，.exe 檔案會從原始程式碼檔案包含其名稱`Sub Main`程序和.dll 檔案會從第一個原始程式檔取得其名稱。</span><span class="sxs-lookup"><span data-stu-id="9fba8-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="9fba8-114">如果您指定沒有.exe 或.dll 副檔名的檔案名稱，編譯器會自動新增延伸模組，根據指定的值`/target`編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="9fba8-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `/target` compiler option.</span></span>  
  
|<span data-ttu-id="9fba8-115">設定/輸出在 Visual Studio 整合式開發環境</span><span class="sxs-lookup"><span data-stu-id="9fba8-115">To set /out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="9fba8-116">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="9fba8-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9fba8-117">在**專案**] 功能表上，按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="9fba8-117">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="9fba8-118">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="9fba8-118">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="9fba8-119">2.按一下 [應用程式] **** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9fba8-119">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="9fba8-120">3.修改中的值**組件名稱**方塊。</span><span class="sxs-lookup"><span data-stu-id="9fba8-120">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9fba8-121">範例</span><span class="sxs-lookup"><span data-stu-id="9fba8-121">Example</span></span>  
 <span data-ttu-id="9fba8-122">下列程式碼編譯`T2.vb`，並建立輸出檔`T2.exe`。</span><span class="sxs-lookup"><span data-stu-id="9fba8-122">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```  
vbc t2.vb /out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="9fba8-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fba8-123">See Also</span></span>  
 <span data-ttu-id="9fba8-124">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="9fba8-124">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="9fba8-125"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="9fba8-125"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="9fba8-126"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="9fba8-126"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
