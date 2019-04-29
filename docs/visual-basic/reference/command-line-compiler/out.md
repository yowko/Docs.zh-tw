---
title: -out (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 5dcf9dc5cc0987e965aba7fd2b8821252e19a655
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788891"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="05265-102">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05265-102">-out (Visual Basic)</span></span>
<span data-ttu-id="05265-103">指定輸出檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="05265-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05265-104">語法</span><span class="sxs-lookup"><span data-stu-id="05265-104">Syntax</span></span>  
  
```  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="05265-105">引數</span><span class="sxs-lookup"><span data-stu-id="05265-105">Arguments</span></span>  
  
|<span data-ttu-id="05265-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="05265-106">Term</span></span>|<span data-ttu-id="05265-107">定義</span><span class="sxs-lookup"><span data-stu-id="05265-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="05265-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="05265-108">Required.</span></span> <span data-ttu-id="05265-109">編譯器會建立輸出檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="05265-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="05265-110">如果檔案名稱包含空格，將名稱括在引號 ("")。</span><span class="sxs-lookup"><span data-stu-id="05265-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05265-111">備註</span><span class="sxs-lookup"><span data-stu-id="05265-111">Remarks</span></span>  
 <span data-ttu-id="05265-112">指定的完整名稱和要建立之檔案的副檔名。</span><span class="sxs-lookup"><span data-stu-id="05265-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="05265-113">如果您不這樣做的.exe 檔案會從原始程式碼檔案包含其名稱`Sub Main`程序和.dll 檔案會從第一個原始程式檔取得其名稱。</span><span class="sxs-lookup"><span data-stu-id="05265-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="05265-114">如果您指定不含.exe 或.dll 副檔名的檔案名稱，編譯器會自動延伸模組會為您加入，根據指定的值`-target`編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="05265-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="05265-115">若要設定-登出 Visual Studio 整合式的開發環境</span><span class="sxs-lookup"><span data-stu-id="05265-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="05265-116">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="05265-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="05265-117">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="05265-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="05265-118">2.按一下 [應用程式]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="05265-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="05265-119">3.修改中的值**組件名稱** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="05265-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="05265-120">範例</span><span class="sxs-lookup"><span data-stu-id="05265-120">Example</span></span>  
 <span data-ttu-id="05265-121">下列程式碼會編譯`T2.vb`，並建立輸出檔`T2.exe`。</span><span class="sxs-lookup"><span data-stu-id="05265-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="05265-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05265-122">See also</span></span>

- [<span data-ttu-id="05265-123">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="05265-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="05265-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05265-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="05265-125">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="05265-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
