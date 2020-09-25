---
description: -baseaddress (C# 編譯器選項)
title: -baseaddress (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: 76da496f7045f12778bba273947b913be1b94e3e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196841"
---
# <a name="-baseaddress-c-compiler-options"></a><span data-ttu-id="b9c1b-103">-baseaddress (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="b9c1b-103">-baseaddress (C# Compiler Options)</span></span>

<span data-ttu-id="b9c1b-104">**-baseaddress** 選項讓您指定要載入 DLL 的慣用基底位址。</span><span class="sxs-lookup"><span data-stu-id="b9c1b-104">The **-baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="b9c1b-105">如需此選項的使用時機與使用原因之詳細資訊，請參閱 [Larry Osterman 的部落格](/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system)。</span><span class="sxs-lookup"><span data-stu-id="b9c1b-105">For more information about when and why to use this option, see [Larry Osterman's WebLog](/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9c1b-106">語法</span><span class="sxs-lookup"><span data-stu-id="b9c1b-106">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="b9c1b-107">引數</span><span class="sxs-lookup"><span data-stu-id="b9c1b-107">Arguments</span></span>  

 `address`  
 <span data-ttu-id="b9c1b-108">DLL 的基底位址。</span><span class="sxs-lookup"><span data-stu-id="b9c1b-108">The base address for the DLL.</span></span> <span data-ttu-id="b9c1b-109">這個位址可以指定十進位、十六進位或八進位數字。</span><span class="sxs-lookup"><span data-stu-id="b9c1b-109">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9c1b-110">備註</span><span class="sxs-lookup"><span data-stu-id="b9c1b-110">Remarks</span></span>  

 <span data-ttu-id="b9c1b-111">DLL 的預設基底位址是由 .NET common language runtime 所設定。</span><span class="sxs-lookup"><span data-stu-id="b9c1b-111">The default base address for a DLL is set by the .NET common language runtime.</span></span>  
  
 <span data-ttu-id="b9c1b-112">請注意，這個位址會去掉低位字。</span><span class="sxs-lookup"><span data-stu-id="b9c1b-112">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="b9c1b-113">例如，如果您指定的是 0x11110001，它會去掉尾數變成 0x11110000。</span><span class="sxs-lookup"><span data-stu-id="b9c1b-113">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="b9c1b-114">若要完成 DLL 的簽章程序，請使用 SN.EXE 和 -R 選項。</span><span class="sxs-lookup"><span data-stu-id="b9c1b-114">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="b9c1b-115">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="b9c1b-115">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="b9c1b-116">開啟專案的 [屬性]\*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="b9c1b-116">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="b9c1b-117">按一下 [建置]\*\*\*\* 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="b9c1b-117">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="b9c1b-118">按一下 [進階]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="b9c1b-118">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="b9c1b-119">修改 **DLL 基底位址**屬性。</span><span class="sxs-lookup"><span data-stu-id="b9c1b-119">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="b9c1b-120">若要以程式設計方式設定這個編譯器選項，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>。</span><span class="sxs-lookup"><span data-stu-id="b9c1b-120">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9c1b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9c1b-121">See also</span></span>

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b9c1b-122">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="b9c1b-122">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="b9c1b-123">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="b9c1b-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
