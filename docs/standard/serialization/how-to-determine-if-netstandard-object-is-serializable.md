---
title: 如何判斷 .NET Standard 物件是否可序列化
description: 示範如何判斷是否可以在執行時間序列化 .NET Standard 型別。
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.openlocfilehash: a425d44ac3b58a568bd51e638f28a2b76ced9dec
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223986"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="66ce5-103">如何判斷 .NET Standard 物件是否可序列化</span><span class="sxs-lookup"><span data-stu-id="66ce5-103">How to determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="66ce5-104">.NET Standard 是一種規格，可定義必須存在於符合該標準版本之特定 .NET 執行的類型和成員。</span><span class="sxs-lookup"><span data-stu-id="66ce5-104">.NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="66ce5-105">但是，.NET Standard 不會定義類型是否可序列化。</span><span class="sxs-lookup"><span data-stu-id="66ce5-105">However, .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="66ce5-106">.NET Standard 程式庫中定義的類型不會以屬性標記 <xref:System.SerializableAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="66ce5-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="66ce5-107">相反地，特定的 .NET 執行（例如 .NET Framework 和 .NET Core）可以用來判斷特定類型是否可序列化。</span><span class="sxs-lookup"><span data-stu-id="66ce5-107">Instead, specific .NET implementations, such as the .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span>

<span data-ttu-id="66ce5-108">如果您已開發以 .NET Standard 為目標的程式庫，則任何支援 .NET Standard 的 .NET 執行都可使用您的程式庫。</span><span class="sxs-lookup"><span data-stu-id="66ce5-108">If you've developed a library that targets .NET Standard, your library can be consumed by any .NET implementation that supports .NET Standard.</span></span> <span data-ttu-id="66ce5-109">這表示您無法事先知道特定類型是否可序列化;您只能判斷它是否可在執行時間進行序列化。</span><span class="sxs-lookup"><span data-stu-id="66ce5-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="66ce5-110">您可以藉由抓取物件 <xref:System.Type.IsSerializable> （代表物件的型別）的屬性值，判斷物件是否可在執行時間進行序列化 <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="66ce5-110">You can determine whether an object is serializable at run time by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="66ce5-111">下列範例提供一個實作為。</span><span class="sxs-lookup"><span data-stu-id="66ce5-111">The following example provides one implementation.</span></span> <span data-ttu-id="66ce5-112">它會定義 `IsSerializable(Object)` 擴充方法，以指出是否 <xref:System.Object> 可以序列化任何實例。</span><span class="sxs-lookup"><span data-stu-id="66ce5-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="66ce5-113">然後，您可以將任何物件傳遞至方法，以判斷是否可以在目前的 .NET 執行上序列化和還原序列化，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="66ce5-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a><span data-ttu-id="66ce5-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66ce5-114">See also</span></span>

- [<span data-ttu-id="66ce5-115">二進位序列化</span><span class="sxs-lookup"><span data-stu-id="66ce5-115">Binary serialization</span></span>](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
