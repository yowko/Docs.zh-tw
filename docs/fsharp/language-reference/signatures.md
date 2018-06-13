---
title: 簽章 (F#)
description: '了解如何使用 F # 簽章檔案，以容納 F # 程式元素，例如類型、 命名空間和模組的一組公開金鑰的簽章資訊。'
ms.date: 05/16/2016
ms.openlocfilehash: 6e182a1a0ac7f3f9fab27026e582d83ee737822e
ms.sourcegitcommit: e5bb395ec86f536e114314184288f40a8c745e2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2018
ms.locfileid: "34149019"
---
# <a name="signatures"></a><span data-ttu-id="a8b50-103">簽章</span><span class="sxs-lookup"><span data-stu-id="a8b50-103">Signatures</span></span>

<span data-ttu-id="a8b50-104">簽章檔案包含一組 F# 程式項目的公開金鑰相關資訊，例如類型、命名空間和模組。</span><span class="sxs-lookup"><span data-stu-id="a8b50-104">A signature file contains information about the public signatures of a set of F# program elements, such as types, namespaces, and modules.</span></span> <span data-ttu-id="a8b50-105">它可用來指定這些程式項目的協助工具。</span><span class="sxs-lookup"><span data-stu-id="a8b50-105">It can be used to specify the accessibility of these program elements.</span></span>


## <a name="remarks"></a><span data-ttu-id="a8b50-106">備註</span><span class="sxs-lookup"><span data-stu-id="a8b50-106">Remarks</span></span>
<span data-ttu-id="a8b50-107">每個 F# 程式碼檔案都可以有一個 *簽章檔案*，它是和程式碼檔案同名的檔案，但副檔名是 .fsi，不是 .fs。</span><span class="sxs-lookup"><span data-stu-id="a8b50-107">For each F# code file, you can have a *signature file*, which is a file that has the same name as the code file but with the extension .fsi instead of .fs.</span></span> <span data-ttu-id="a8b50-108">如果直接使用命令列，也可以在命令列編譯中加入簽章檔案。</span><span class="sxs-lookup"><span data-stu-id="a8b50-108">Signature files can also be added to the compilation command-line if you are using the command line directly.</span></span> <span data-ttu-id="a8b50-109">為區別程式碼檔案和簽章檔案，程式碼檔案有時稱為 *實作檔案*。</span><span class="sxs-lookup"><span data-stu-id="a8b50-109">To distinguish between code files and signature files, code files are sometimes referred to as *implementation files*.</span></span> <span data-ttu-id="a8b50-110">在專案中，簽章檔案應該位在相關聯的程式碼檔案之前。</span><span class="sxs-lookup"><span data-stu-id="a8b50-110">In a project, the signature file should precede the associated code file.</span></span>

<span data-ttu-id="a8b50-111">簽章檔案描述對應實作檔案中的命名空間、模組、類型和成員。</span><span class="sxs-lookup"><span data-stu-id="a8b50-111">A signature file describes the namespaces, modules, types, and members in the corresponding implementation file.</span></span> <span data-ttu-id="a8b50-112">您使用簽章檔案中的資訊，指定在對應的實作檔案中，哪些程式碼部分可以從實作檔案外部的程式碼存取，哪些部分從實作檔案內部的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="a8b50-112">You use the information in a signature file to specify what parts of the code in the corresponding implementation file can be accessed from code outside the implementation file, and what parts are internal to the implementation file.</span></span> <span data-ttu-id="a8b50-113">簽章檔案包含的命名空間、模組和類型，必須是實作檔案所包含之命名空間、模組和類型的子集。</span><span class="sxs-lookup"><span data-stu-id="a8b50-113">The namespaces, modules, and types that are included in the signature file must be a subset of the namespaces, modules, and types that are included in the implementation file.</span></span> <span data-ttu-id="a8b50-114">加上本主題稍後列出的某些例外狀況，簽章檔案中沒有列出的那些語言項目會被實作檔案視為私用的。</span><span class="sxs-lookup"><span data-stu-id="a8b50-114">With some exceptions noted later in this topic, those language elements that are not listed in the signature file are considered private to the implementation file.</span></span> <span data-ttu-id="a8b50-115">如果專案或命令列中找不到簽章檔，會使用預設的協助工具。</span><span class="sxs-lookup"><span data-stu-id="a8b50-115">If no signature file is found in the project or command line, the default accessibility is used.</span></span>

<span data-ttu-id="a8b50-116">如需預設協助工具的詳細資訊，請參閱[存取控制](access-control.md)。</span><span class="sxs-lookup"><span data-stu-id="a8b50-116">For more information about the default accessibility, see [Access Control](access-control.md).</span></span>

<span data-ttu-id="a8b50-117">在簽章檔案中，不用重複類型定義以及每個方法或函式的實作。</span><span class="sxs-lookup"><span data-stu-id="a8b50-117">In a signature file, you do not repeat the definition of the types and the implementations of each method or function.</span></span> <span data-ttu-id="a8b50-118">而要使用每個方法和函式的簽章，做為模組或命名空間片段實作功能的完整規格。</span><span class="sxs-lookup"><span data-stu-id="a8b50-118">Instead, you use the signature for each method and function, which acts as a complete specification of the functionality that is implemented by a module or namespace fragment.</span></span> <span data-ttu-id="a8b50-119">類型簽章的語法與介面和抽象類別的抽象方法宣告中使用的語法一樣，當它正確顯示編譯的輸入時，也是由 IntelliSense 和 F# 解譯器 fsi.exe 顯示。</span><span class="sxs-lookup"><span data-stu-id="a8b50-119">The syntax for a type signature is the same as that used in abstract method declarations in interfaces and abstract classes, and is also shown by IntelliSense and by the F# interpreter fsi.exe when it displays correctly compiled input.</span></span>

<span data-ttu-id="a8b50-120">如果類型簽章的資訊不足以指出類型是否已密封，或是否為介面類型，您就必須在編譯器中加入表示類型本質的屬性。</span><span class="sxs-lookup"><span data-stu-id="a8b50-120">If there is not enough information in the type signature to indicate whether a type is sealed, or whether it is an interface type, you must add an attribute that indicates the nature of the type to the compiler.</span></span> <span data-ttu-id="a8b50-121">下表說明這種用途的屬性。</span><span class="sxs-lookup"><span data-stu-id="a8b50-121">Attributes that you use for this purpose are described in the following table.</span></span>



|<span data-ttu-id="a8b50-122">屬性</span><span class="sxs-lookup"><span data-stu-id="a8b50-122">Attribute</span></span>|<span data-ttu-id="a8b50-123">描述</span><span class="sxs-lookup"><span data-stu-id="a8b50-123">Description</span></span>|
|---------|-----------|
|`[<Sealed>]`|<span data-ttu-id="a8b50-124">用於沒有任何抽象成員的類型，或不應該擴充的類型。</span><span class="sxs-lookup"><span data-stu-id="a8b50-124">For a type that has no abstract members, or that should not be extended.</span></span>|
|`[<Interface>]`|<span data-ttu-id="a8b50-125">用於介面類型。</span><span class="sxs-lookup"><span data-stu-id="a8b50-125">For a type that is an interface.</span></span>|
<span data-ttu-id="a8b50-126">如果實作檔案之簽章和宣告間的屬性不一致，編譯器就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="a8b50-126">The compiler produces an error if the attributes are not consistent between the signature and the declaration in the implementation file.</span></span>

<span data-ttu-id="a8b50-127">使用關鍵字 `val` 建立值或函式值的簽章。</span><span class="sxs-lookup"><span data-stu-id="a8b50-127">Use the keyword `val` to create a signature for a value or function value.</span></span> <span data-ttu-id="a8b50-128">關鍵字 `type` 引進類型簽章。</span><span class="sxs-lookup"><span data-stu-id="a8b50-128">The keyword `type` introduces a type signature.</span></span>

<span data-ttu-id="a8b50-129">您可以使用 `--sig` 編譯器選項產生簽章檔案。</span><span class="sxs-lookup"><span data-stu-id="a8b50-129">You can generate a signature file by using the `--sig` compiler option.</span></span> <span data-ttu-id="a8b50-130">一般而言，不用手動撰寫 .fsi 檔案。</span><span class="sxs-lookup"><span data-stu-id="a8b50-130">Generally, you do not write .fsi files manually.</span></span> <span data-ttu-id="a8b50-131">而是使用編譯器產生 .fsi 檔案，將它們加入您的專案 (如有)，然後移除您不想存取的方法和函式來編輯這些檔案。</span><span class="sxs-lookup"><span data-stu-id="a8b50-131">Instead, you generate .fsi files by using the compiler, add them to your project, if you have one, and edit them by removing methods and functions that you do not want to be accessible.</span></span>

<span data-ttu-id="a8b50-132">類型簽章有數個規則：</span><span class="sxs-lookup"><span data-stu-id="a8b50-132">There are several rules for type signatures:</span></span>


- <span data-ttu-id="a8b50-133">實作檔案中的類型縮寫絕不能符合簽章檔案中沒有縮寫的類型。</span><span class="sxs-lookup"><span data-stu-id="a8b50-133">Type abbreviations in an implementation file must not match a type without an abbreviation in a signature file.</span></span>


- <span data-ttu-id="a8b50-134">記錄和差別聯集必須全部公開或不公開欄位和建構函式，而簽章中的順序必須符合實作檔案中的順序。</span><span class="sxs-lookup"><span data-stu-id="a8b50-134">Records and discriminated unions must expose either all or none of their fields and constructors, and the order in the signature must match the order in the implementation file.</span></span> <span data-ttu-id="a8b50-135">類別會顯示簽章的部分、全部欄位和方法，或完全不顯示。</span><span class="sxs-lookup"><span data-stu-id="a8b50-135">Classes can reveal some, all, or none of their fields and methods in the signature.</span></span>


- <span data-ttu-id="a8b50-136">具有建構函式的類別和結構必須公開其基底類別的宣告 ( `inherits` 宣告)。</span><span class="sxs-lookup"><span data-stu-id="a8b50-136">Classes and structures that have constructors must expose the declarations of their base classes (the `inherits` declaration).</span></span> <span data-ttu-id="a8b50-137">此外，具有建構函式的類別和結構必須公開所有的抽象方法和介面宣告。</span><span class="sxs-lookup"><span data-stu-id="a8b50-137">Also, classes and structures that have constructors must expose all of their abstract methods and interface declarations.</span></span>


- <span data-ttu-id="a8b50-138">介面類型必須顯示所有的方法和介面。</span><span class="sxs-lookup"><span data-stu-id="a8b50-138">Interface types must reveal all their methods and interfaces.</span></span>


<span data-ttu-id="a8b50-139">值簽章的規則如下：</span><span class="sxs-lookup"><span data-stu-id="a8b50-139">The rules for value signatures are as follows:</span></span>


- <span data-ttu-id="a8b50-140">協助工具修飾詞 (`public`、 `internal`等等) 和簽章中的 `inline` 及 `mutable` 修飾詞必須符合實作中的修飾詞。</span><span class="sxs-lookup"><span data-stu-id="a8b50-140">Modifiers for accessibility (`public`, `internal`, and so on) and the `inline` and `mutable` modifiers in the signature must match those in the implementation.</span></span>


- <span data-ttu-id="a8b50-141">泛型類型參數 (無論是推斷隱含或明確宣告) 的數目必須相符，而且泛型類型參數中的類型和類型條件約束必須相符。</span><span class="sxs-lookup"><span data-stu-id="a8b50-141">The number of generic type parameters (either implicitly inferred or explicitly declared) must match, and the types and type constraints in generic type parameters must match.</span></span>


- <span data-ttu-id="a8b50-142">如果使用了 `Literal` 屬性，它必須同時出現在簽章和實作中，而且兩者都必須使用相同的常值。</span><span class="sxs-lookup"><span data-stu-id="a8b50-142">If the `Literal` attribute is used, it must appear in both the signature and the implementation, and the same literal value must be used for both.</span></span>


- <span data-ttu-id="a8b50-143">簽章及實作的參數模式 (也稱為 *Arity*) 必須一致。</span><span class="sxs-lookup"><span data-stu-id="a8b50-143">The pattern of parameters (also known as the *arity*) of signatures and implementations must be consistent.</span></span>


- <span data-ttu-id="a8b50-144">如果簽章檔案中的參數名稱與對應的實作檔案不同，簽章檔案中的名稱將會改用，這可能會造成偵錯或分析時的問題。</span><span class="sxs-lookup"><span data-stu-id="a8b50-144">If parameter names in a signature file differ from the corresponding implementation file, the name in the signature file will be used instead, which may cause issues when debugging or profiling.</span></span> <span data-ttu-id="a8b50-145">如果您想要接收這類不符，啟用警告 3218 專案檔中的通知，或叫用編譯器時 (請參閱`--warnon`下[編譯器選項](compiler-options.md))。</span><span class="sxs-lookup"><span data-stu-id="a8b50-145">If you wish to be notified of such mismatches, enable warning 3218 in your project file or when invoking the compiler (see `--warnon` under [Compiler Options](compiler-options.md)).</span></span>


<span data-ttu-id="a8b50-146">下列程式碼範例顯示的簽章檔案範例，具有命名空間、模組、函式值和有適當屬性的類型簽章。</span><span class="sxs-lookup"><span data-stu-id="a8b50-146">The following code example shows an example of a signature file that has namespace, module, function value, and type signatures together with the appropriate attributes.</span></span> <span data-ttu-id="a8b50-147">它也顯示對應的實作檔案。</span><span class="sxs-lookup"><span data-stu-id="a8b50-147">It also shows the corresponding implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9002.fs)]

<span data-ttu-id="a8b50-148">下列程式碼顯示實作檔案。</span><span class="sxs-lookup"><span data-stu-id="a8b50-148">The following code shows the implementation file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssignatures/snippet9001.fs)]
    
## <a name="see-also"></a><span data-ttu-id="a8b50-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8b50-149">See Also</span></span>
[<span data-ttu-id="a8b50-150">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="a8b50-150">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="a8b50-151">存取控制</span><span class="sxs-lookup"><span data-stu-id="a8b50-151">Access Control</span></span>](access-control.md)

[<span data-ttu-id="a8b50-152">編譯器選項</span><span class="sxs-lookup"><span data-stu-id="a8b50-152">Compiler Options</span></span>](compiler-options.md)
