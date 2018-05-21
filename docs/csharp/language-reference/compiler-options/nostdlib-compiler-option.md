---
title: -nostdlib (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 1dc0ab70ca28626c4a3f505c13ec1d6f828a4b05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="eeb6e-102">-nostdlib (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="eeb6e-102">-nostdlib (C# Compiler Options)</span></span>
<span data-ttu-id="eeb6e-103">**-nostdlib** 會導致無法匯入 mscorlib.dll，而此檔案定義整個系統命名空間。</span><span class="sxs-lookup"><span data-stu-id="eeb6e-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eeb6e-104">語法</span><span class="sxs-lookup"><span data-stu-id="eeb6e-104">Syntax</span></span>  
  
```console  
-nostdlib[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="eeb6e-105">備註</span><span class="sxs-lookup"><span data-stu-id="eeb6e-105">Remarks</span></span>  
 <span data-ttu-id="eeb6e-106">如果您想要定義或建立自己的系統命名空間和物件，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="eeb6e-106">Use this option if you want to define or create your own System namespace and objects.</span></span>  
  
 <span data-ttu-id="eeb6e-107">如果您未指定 **-nostdlib**，則 mscorlib.dll 會匯入至您的程式 (與指定 **-nostdlib-** 相容)。</span><span class="sxs-lookup"><span data-stu-id="eeb6e-107">If you do not specify **-nostdlib**, mscorlib.dll will be imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="eeb6e-108">指定 **-nostdlib** 等同於指定 **-nostdlib+**。</span><span class="sxs-lookup"><span data-stu-id="eeb6e-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="eeb6e-109">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="eeb6e-109">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="eeb6e-110">開啟專案的 [屬性]  頁面。</span><span class="sxs-lookup"><span data-stu-id="eeb6e-110">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="eeb6e-111">按一下 [建置]  屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="eeb6e-111">Click the **Build** properties page.</span></span>  
  
3.  <span data-ttu-id="eeb6e-112">按一下 [ **進階** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="eeb6e-112">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="eeb6e-113">修改 [不要參考 mscorlib.dll]  屬性。</span><span class="sxs-lookup"><span data-stu-id="eeb6e-113">Modify the **Do not reference mscorlib.dll** property.</span></span>  
  
 <span data-ttu-id="eeb6e-114">如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>。</span><span class="sxs-lookup"><span data-stu-id="eeb6e-114">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeb6e-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="eeb6e-115">See Also</span></span>  
 [<span data-ttu-id="eeb6e-116">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="eeb6e-116">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
