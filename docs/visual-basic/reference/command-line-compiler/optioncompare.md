---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: ed9adc7cddd9eb204937b9819e4eeff176821e95
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400550"
---
# <a name="-optioncompare"></a><span data-ttu-id="acb67-102">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="acb67-102">-optioncompare</span></span>

<span data-ttu-id="acb67-103">指定如何進行字串比較。</span><span class="sxs-lookup"><span data-stu-id="acb67-103">Specifies how string comparisons are made.</span></span>

## <a name="syntax"></a><span data-ttu-id="acb67-104">語法</span><span class="sxs-lookup"><span data-stu-id="acb67-104">Syntax</span></span>

```console
-optioncompare:{binary | text}
```

## <a name="remarks"></a><span data-ttu-id="acb67-105">備註</span><span class="sxs-lookup"><span data-stu-id="acb67-105">Remarks</span></span>

<span data-ttu-id="acb67-106">您可以指定 `-optioncompare` 兩種形式的其中一種： `-optioncompare:binary` 使用二進位字串比較，並 `-optioncompare:text` 使用文字字串比較。</span><span class="sxs-lookup"><span data-stu-id="acb67-106">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="acb67-107">根據預設，編譯器會使用 `-optioncompare:binary` 。</span><span class="sxs-lookup"><span data-stu-id="acb67-107">By default, the compiler uses `-optioncompare:binary`.</span></span>

<span data-ttu-id="acb67-108">在 Microsoft Windows 中，目前的字碼頁會決定二進位排序次序。</span><span class="sxs-lookup"><span data-stu-id="acb67-108">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="acb67-109">典型的二進位排序次序如下所示：</span><span class="sxs-lookup"><span data-stu-id="acb67-109">A typical binary sort order is as follows:</span></span>

`A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

<span data-ttu-id="acb67-110">以文字為基礎的字串比較是以您系統的地區設定所決定的不區分大小寫文字排序次序為基礎。</span><span class="sxs-lookup"><span data-stu-id="acb67-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="acb67-111">一般文字排序次序如下所示：</span><span class="sxs-lookup"><span data-stu-id="acb67-111">A typical text sort order is as follows:</span></span>

`(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`

### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="acb67-112">若要在 Visual Studio IDE 中設定-optioncompare</span><span class="sxs-lookup"><span data-stu-id="acb67-112">To set -optioncompare in the Visual Studio IDE</span></span>

1. <span data-ttu-id="acb67-113">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="acb67-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="acb67-114">按一下 [專案]\*\*\*\* 功能表上的 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="acb67-114">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="acb67-115">按一下 [編譯]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="acb67-115">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="acb67-116">修改 [**選項比較**] 方塊中的值。</span><span class="sxs-lookup"><span data-stu-id="acb67-116">Modify the value in the **Option Compare** box.</span></span>

### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="acb67-117">以程式設計方式設定-optioncompare</span><span class="sxs-lookup"><span data-stu-id="acb67-117">To set -optioncompare programmatically</span></span>

<span data-ttu-id="acb67-118">請參閱[Option Compare 語句](../../language-reference/statements/option-compare-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="acb67-118">See [Option Compare Statement](../../language-reference/statements/option-compare-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="acb67-119">範例</span><span class="sxs-lookup"><span data-stu-id="acb67-119">Example</span></span>

<span data-ttu-id="acb67-120">下列程式碼會編譯 `ProjFile.vb` 並使用二進位字串比較。</span><span class="sxs-lookup"><span data-stu-id="acb67-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>

```console
vbc -optioncompare:binary projFile.vb
```

## <a name="see-also"></a><span data-ttu-id="acb67-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acb67-121">See also</span></span>

- [<span data-ttu-id="acb67-122">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="acb67-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="acb67-123">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="acb67-123">-optionexplicit</span></span>](optionexplicit.md)
- [<span data-ttu-id="acb67-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="acb67-124">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="acb67-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="acb67-125">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="acb67-126">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="acb67-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="acb67-127">Option Compare 陳述式</span><span class="sxs-lookup"><span data-stu-id="acb67-127">Option Compare Statement</span></span>](../../language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="acb67-128">選項對話方塊、專案、Visual Basic 預設值</span><span class="sxs-lookup"><span data-stu-id="acb67-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
