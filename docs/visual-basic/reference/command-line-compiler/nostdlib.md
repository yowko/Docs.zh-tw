---
title: -nostdlib
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 0934799853323110e73087ba6d8975c30f84d8f7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387708"
---
# <a name="-nostdlib-visual-basic"></a><span data-ttu-id="a89e5-102">-nostdlib （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="a89e5-102">-nostdlib (Visual Basic)</span></span>
<span data-ttu-id="a89e5-103">導致編譯器不自動參考標準程式庫。</span><span class="sxs-lookup"><span data-stu-id="a89e5-103">Causes the compiler not to automatically reference the standard libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a89e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="a89e5-104">Syntax</span></span>  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a><span data-ttu-id="a89e5-105">備註</span><span class="sxs-lookup"><span data-stu-id="a89e5-105">Remarks</span></span>  
 <span data-ttu-id="a89e5-106">`-nostdlib`選項會移除對 system.object 元件的自動參考，並防止編譯器讀取 Vbc .rsp 檔案。</span><span class="sxs-lookup"><span data-stu-id="a89e5-106">The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file.</span></span> <span data-ttu-id="a89e5-107">與 Vbc 檔案位於相同目錄中的 Vbc .rsp 檔案，會參考常用的 .NET Framework 元件，並匯入 `System` 和 `Microsoft.VisualBasic` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="a89e5-107">The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a89e5-108">我們一律會參考 Mscorlib.dll 和 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="a89e5-108">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a89e5-109">此 `-nostdlib` 選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="a89e5-109">The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a89e5-110">範例</span><span class="sxs-lookup"><span data-stu-id="a89e5-110">Example</span></span>  
 <span data-ttu-id="a89e5-111">下列程式碼會進行編譯， `T2.vb` 而不會參考標準程式庫。</span><span class="sxs-lookup"><span data-stu-id="a89e5-111">The following code compiles `T2.vb` without referencing the standard libraries.</span></span> <span data-ttu-id="a89e5-112">您必須將 `_MYTYPE` 條件式編譯常數設定為字串 "Empty"，才能移除該 `My` 物件。</span><span class="sxs-lookup"><span data-stu-id="a89e5-112">You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.</span></span>  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a89e5-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a89e5-113">See also</span></span>

- [<span data-ttu-id="a89e5-114">-noconfig</span><span class="sxs-lookup"><span data-stu-id="a89e5-114">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="a89e5-115">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="a89e5-115">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="a89e5-116">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="a89e5-116">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="a89e5-117">自訂 My 可以使用的物件</span><span class="sxs-lookup"><span data-stu-id="a89e5-117">Customizing Which Objects are Available in My</span></span>](../../developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
