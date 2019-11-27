---
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 67366e13e4dceea4772d0730222413cb25b4e8b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352380"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="8c947-102">-out （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="8c947-102">-out (Visual Basic)</span></span>
<span data-ttu-id="8c947-103">指定輸出檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="8c947-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c947-104">語法</span><span class="sxs-lookup"><span data-stu-id="8c947-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="8c947-105">引數</span><span class="sxs-lookup"><span data-stu-id="8c947-105">Arguments</span></span>  
  
|<span data-ttu-id="8c947-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="8c947-106">Term</span></span>|<span data-ttu-id="8c947-107">定義</span><span class="sxs-lookup"><span data-stu-id="8c947-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="8c947-108">必要。</span><span class="sxs-lookup"><span data-stu-id="8c947-108">Required.</span></span> <span data-ttu-id="8c947-109">編譯器所建立之輸出檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="8c947-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="8c947-110">如果檔案名包含空格，請將名稱括在引號（""）中。</span><span class="sxs-lookup"><span data-stu-id="8c947-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c947-111">備註</span><span class="sxs-lookup"><span data-stu-id="8c947-111">Remarks</span></span>  
 <span data-ttu-id="8c947-112">指定要建立之檔案的完整名稱和副檔名。</span><span class="sxs-lookup"><span data-stu-id="8c947-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="8c947-113">如果不這麼做，.exe 檔案會從包含 `Sub Main` 程式的原始程式碼檔取得其名稱，而 .dll 檔案會從第一個原始程式碼檔案取得其名稱。</span><span class="sxs-lookup"><span data-stu-id="8c947-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="8c947-114">如果您指定不含 .exe 或 .dll 副檔名的檔案名，編譯器會自動為您加入延伸模組，視針對 `-target` 編譯器選項所指定的值而定。</span><span class="sxs-lookup"><span data-stu-id="8c947-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="8c947-115">在 Visual Studio 的整合式開發環境中設定</span><span class="sxs-lookup"><span data-stu-id="8c947-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="8c947-116">1. 在**方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="8c947-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8c947-117">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="8c947-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="8c947-118">2. 按一下 [**應用程式**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8c947-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="8c947-119">3. 修改 [**元件名稱**] 方塊中的值。</span><span class="sxs-lookup"><span data-stu-id="8c947-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8c947-120">範例</span><span class="sxs-lookup"><span data-stu-id="8c947-120">Example</span></span>  
 <span data-ttu-id="8c947-121">下列程式碼會編譯 `T2.vb` 並建立 `T2.exe`的輸出檔。</span><span class="sxs-lookup"><span data-stu-id="8c947-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c947-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="8c947-122">See also</span></span>

- [<span data-ttu-id="8c947-123">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="8c947-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="8c947-124">-target （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="8c947-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="8c947-125">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="8c947-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
