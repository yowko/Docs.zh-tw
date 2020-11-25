---
ms.openlocfilehash: 394f2daebad7b6af94bee4d7876796e87fe8ab19
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031996"
---
### <a name="handling-corrupted-state-exceptions-is-not-supported"></a><span data-ttu-id="01add-101">不支援處理損毀狀態例外狀況</span><span class="sxs-lookup"><span data-stu-id="01add-101">Handling corrupted state exceptions is not supported</span></span>

<span data-ttu-id="01add-102">不支援在 .NET Core 中處理損毀的進程狀態例外狀況。</span><span class="sxs-lookup"><span data-stu-id="01add-102">Handling corrupted-process-state exceptions in .NET Core is not supported.</span></span>

#### <a name="change-description"></a><span data-ttu-id="01add-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="01add-103">Change description</span></span>

<span data-ttu-id="01add-104">先前，managed 程式碼例外狀況處理常式可能會攔截並處理損毀進程狀態的例外狀況，例如，使用 c # 中的 [try catch](../../../../docs/csharp/language-reference/keywords/try-catch.md) 語句。</span><span class="sxs-lookup"><span data-stu-id="01add-104">Previously, corrupted-process-state exceptions could be caught and handled by managed code exception handlers, for example, by using a [try-catch](../../../../docs/csharp/language-reference/keywords/try-catch.md) statement in C#.</span></span>

<span data-ttu-id="01add-105">從 .NET Core 1.0 開始，managed 程式碼無法處理損毀進程狀態的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="01add-105">Starting in .NET Core 1.0, corrupted-process-state exceptions cannot be handled by managed code.</span></span> <span data-ttu-id="01add-106">Common language runtime 不會將損毀進程狀態的例外狀況傳遞給 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="01add-106">The common language runtime doesn't deliver corrupted-process-state exceptions to managed code.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="01add-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="01add-107">Version introduced</span></span>

<span data-ttu-id="01add-108">1.0</span><span class="sxs-lookup"><span data-stu-id="01add-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="01add-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="01add-109">Recommended action</span></span>

<span data-ttu-id="01add-110">藉由解決導致這些例外狀況的情況，以避免需要處理損毀進程狀態的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="01add-110">Avoid the need to handle corrupted-process-state exceptions by addressing the situations that lead to them instead.</span></span> <span data-ttu-id="01add-111">如果絕對必須處理已損毀的進程狀態例外狀況，請在 C 或 c + + 程式碼中撰寫例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="01add-111">If it's absolutely necessary to handle corrupted-process-state exceptions, write the exception handler in C or C++ code.</span></span>

#### <a name="category"></a><span data-ttu-id="01add-112">類別</span><span class="sxs-lookup"><span data-stu-id="01add-112">Category</span></span>

<span data-ttu-id="01add-113">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="01add-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="01add-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="01add-114">Affected APIs</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName>
- [<span data-ttu-id="01add-115">legacyCorruptedStateExceptionsPolicy 項目</span><span class="sxs-lookup"><span data-stu-id="01add-115">legacyCorruptedStateExceptionsPolicy element</span></span>](~/docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)

<!--

#### Affected APIs

- `T:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute`

-->
