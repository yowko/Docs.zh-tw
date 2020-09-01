---
description: -nostdlib (C# 編譯器選項)
title: -nostdlib (C# 編譯器選項)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 214918b32f1f1276eb936e66daba3d372a1e9228
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125094"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="7d7ca-103">-nostdlib (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="7d7ca-103">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="7d7ca-104">**-nostdlib** 會導致無法匯入 mscorlib.dll，而此檔案定義整個系統命名空間。</span><span class="sxs-lookup"><span data-stu-id="7d7ca-104">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="7d7ca-105">語法</span><span class="sxs-lookup"><span data-stu-id="7d7ca-105">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="7d7ca-106">備註</span><span class="sxs-lookup"><span data-stu-id="7d7ca-106">Remarks</span></span>

<span data-ttu-id="7d7ca-107">如果您想要定義或建立自己的系統命名空間和物件，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="7d7ca-107">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="7d7ca-108">若您沒有指定 **-nostdlib**，mscorlib.dll 會匯入您的程式中 (與指定 **-nostdlib-** 相同)。</span><span class="sxs-lookup"><span data-stu-id="7d7ca-108">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="7d7ca-109">指定 **-nostdlib** 等同於指定 **-nostdlib+**。</span><span class="sxs-lookup"><span data-stu-id="7d7ca-109">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="7d7ca-110">在 Visual Studio 中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="7d7ca-110">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="7d7ca-111">下列指示僅適用於 Visual Studio 2015 (及更早版本)。</span><span class="sxs-lookup"><span data-stu-id="7d7ca-111">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="7d7ca-112">較新版本的 Visual Studio 中不存在 [ **不參考] mscorlib.dll** 組建屬性。</span><span class="sxs-lookup"><span data-stu-id="7d7ca-112">The **Do not reference mscorlib.dll** build property doesn't exist in newer versions of Visual Studio.</span></span>

1. <span data-ttu-id="7d7ca-113">開啟專案的 [屬性] \*\*\*\* 頁面。</span><span class="sxs-lookup"><span data-stu-id="7d7ca-113">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="7d7ca-114">按一下 [建置] \*\*\*\* 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="7d7ca-114">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="7d7ca-115">按一下 [進階]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="7d7ca-115">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="7d7ca-116">修改 [不要參考 mscorlib.dll] \*\*\*\* 屬性。</span><span class="sxs-lookup"><span data-stu-id="7d7ca-116">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="7d7ca-117">若要以程式方式設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="7d7ca-117">To set this compiler option programmatically</span></span>

<span data-ttu-id="7d7ca-118">如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>。</span><span class="sxs-lookup"><span data-stu-id="7d7ca-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d7ca-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d7ca-119">See also</span></span>

- [<span data-ttu-id="7d7ca-120">C # 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="7d7ca-120">C# Compiler Options</span></span>](./index.md)
