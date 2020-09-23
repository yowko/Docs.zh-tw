---
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 7c013270c8a6b7c2b28f02766df7437b43075dd2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098900"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="9c530-102">-out (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="9c530-102">-out (Visual Basic)</span></span>

<span data-ttu-id="9c530-103">指定輸出檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c530-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c530-104">語法</span><span class="sxs-lookup"><span data-stu-id="9c530-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="9c530-105">引數</span><span class="sxs-lookup"><span data-stu-id="9c530-105">Arguments</span></span>  
  
|<span data-ttu-id="9c530-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="9c530-106">Term</span></span>|<span data-ttu-id="9c530-107">定義</span><span class="sxs-lookup"><span data-stu-id="9c530-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="9c530-108">必要。</span><span class="sxs-lookup"><span data-stu-id="9c530-108">Required.</span></span> <span data-ttu-id="9c530-109">編譯器所建立之輸出檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c530-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="9c530-110">如果檔案名包含空格，請用引號括住名稱 ( "" ) 。</span><span class="sxs-lookup"><span data-stu-id="9c530-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c530-111">備註</span><span class="sxs-lookup"><span data-stu-id="9c530-111">Remarks</span></span>  

 <span data-ttu-id="9c530-112">指定要建立之檔案的完整名稱和副檔名。</span><span class="sxs-lookup"><span data-stu-id="9c530-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="9c530-113">如果不這麼做，.exe 檔會從包含程式的原始程式碼檔案取得其名稱 `Sub Main` ，而 .dll 檔會從第一個原始程式碼檔案取得其名稱。</span><span class="sxs-lookup"><span data-stu-id="9c530-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="9c530-114">如果您指定的檔案名沒有 .exe 或 .dll 副檔名，編譯器會自動為您加入副檔名，視編譯器選項指定的值而定 `-target` 。</span><span class="sxs-lookup"><span data-stu-id="9c530-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="9c530-115">若要在 Visual Studio 整合式開發環境中進行設定</span><span class="sxs-lookup"><span data-stu-id="9c530-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="9c530-116">1. 在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="9c530-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9c530-117">按一下 [專案] 功能表上的 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="9c530-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="9c530-118">2. 按一下 [ **應用程式** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9c530-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="9c530-119">3. 修改 [ **元件名稱** ] 方塊中的值。</span><span class="sxs-lookup"><span data-stu-id="9c530-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9c530-120">範例</span><span class="sxs-lookup"><span data-stu-id="9c530-120">Example</span></span>  

 <span data-ttu-id="9c530-121">下列程式碼會編譯 `T2.vb` 並建立輸出檔 `T2.exe` 。</span><span class="sxs-lookup"><span data-stu-id="9c530-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c530-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c530-122">See also</span></span>

- [<span data-ttu-id="9c530-123">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="9c530-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="9c530-124">-目標 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="9c530-124">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="9c530-125">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="9c530-125">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
