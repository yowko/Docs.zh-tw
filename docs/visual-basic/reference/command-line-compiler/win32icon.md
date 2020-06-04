---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: 52ef0b991554c800dba4320b0c64c81ddd1b0ff4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414281"
---
# <a name="-win32icon"></a><span data-ttu-id="7ab28-102">-win32icon</span><span class="sxs-lookup"><span data-stu-id="7ab28-102">-win32icon</span></span>
<span data-ttu-id="7ab28-103">在輸出檔中插入 .ico 檔案。</span><span class="sxs-lookup"><span data-stu-id="7ab28-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="7ab28-104">這個 .ico 檔案代表檔案**瀏覽器**中的輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="7ab28-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ab28-105">語法</span><span class="sxs-lookup"><span data-stu-id="7ab28-105">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="7ab28-106">引數</span><span class="sxs-lookup"><span data-stu-id="7ab28-106">Arguments</span></span>  
  
|<span data-ttu-id="7ab28-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="7ab28-107">Term</span></span>|<span data-ttu-id="7ab28-108">定義</span><span class="sxs-lookup"><span data-stu-id="7ab28-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="7ab28-109">要加入至輸出檔的 .ico 檔案。</span><span class="sxs-lookup"><span data-stu-id="7ab28-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="7ab28-110">將檔案名括在引號（""）中（如果它包含空格）。</span><span class="sxs-lookup"><span data-stu-id="7ab28-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ab28-111">備註</span><span class="sxs-lookup"><span data-stu-id="7ab28-111">Remarks</span></span>  
 <span data-ttu-id="7ab28-112">您可以使用 Microsoft Windows 資源編譯器（RC）來建立 .ico 檔案。</span><span class="sxs-lookup"><span data-stu-id="7ab28-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="7ab28-113">當您編譯 Visual C++ 程式時，會叫用資源編譯器;會從 .rc 檔案建立 .ico 檔案。</span><span class="sxs-lookup"><span data-stu-id="7ab28-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="7ab28-114">`-win32icon` 和 `-win32resource` 選項互斥。</span><span class="sxs-lookup"><span data-stu-id="7ab28-114">The `-win32icon` and `-win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="7ab28-115">請參閱[-linkresource （Visual Basic）](linkresource.md)來參考 .NET Framework 資源檔，或使用[-resource （Visual Basic）](resource.md)來附加 .NET Framework 資源檔。</span><span class="sxs-lookup"><span data-stu-id="7ab28-115">See [-linkresource (Visual Basic)](linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](resource.md) to attach a .NET Framework resource file.</span></span> <span data-ttu-id="7ab28-116">請參閱[-win32resource](win32resource.md)以匯入 .res 檔案。</span><span class="sxs-lookup"><span data-stu-id="7ab28-116">See [-win32resource](win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="7ab28-117">若要在 Visual Studio IDE 中設定-win32icon</span><span class="sxs-lookup"><span data-stu-id="7ab28-117">To set -win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="7ab28-118">1. 在**方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="7ab28-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="7ab28-119">按一下 [專案]\*\*\*\* 功能表上的 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7ab28-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="7ab28-120">2. 按一下 [**應用程式**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7ab28-120">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="7ab28-121">3. 修改 [**圖示**] 方塊中的值。</span><span class="sxs-lookup"><span data-stu-id="7ab28-121">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7ab28-122">範例</span><span class="sxs-lookup"><span data-stu-id="7ab28-122">Example</span></span>  
 <span data-ttu-id="7ab28-123">下列程式碼會編譯 `In.vb` 並附加 .ico 檔案 `Rf.ico` 。</span><span class="sxs-lookup"><span data-stu-id="7ab28-123">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7ab28-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ab28-124">See also</span></span>

- [<span data-ttu-id="7ab28-125">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="7ab28-125">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="7ab28-126">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="7ab28-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
