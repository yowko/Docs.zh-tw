---
title: 如何判斷 .NET Standard 物件是否可序列化
description: 顯示如何判斷在執行時間是否可以序列化 .NET Standard 類型。
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.openlocfilehash: b6791ae0666aeb0ac02d8a38ca419d7de2b263cf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289599"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="75e62-103">如何判斷 .NET Standard 物件是否可序列化</span><span class="sxs-lookup"><span data-stu-id="75e62-103">How to determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="75e62-104">.NET Standard 是一項規格，定義必須存在於符合該標準版本之特定 .NET 部署上的類型和成員。</span><span class="sxs-lookup"><span data-stu-id="75e62-104">The .NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="75e62-105">不過，.NET Standard 不會定義型別是否為可序列化。</span><span class="sxs-lookup"><span data-stu-id="75e62-105">However, the .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="75e62-106">.NET Standard 程式庫中定義的類型不會以屬性標記 <xref:System.SerializableAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="75e62-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="75e62-107">相反地，特定的 .NET 部署（例如 .NET Framework 和 .NET Core）可自由判斷特定類型是否可序列化。</span><span class="sxs-lookup"><span data-stu-id="75e62-107">Instead, specific .NET implementations, such as the .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span>

<span data-ttu-id="75e62-108">如果您已開發以 .NET Standard 為目標的程式庫，則任何支援 .NET Standard 的 .NET 部署都可以使用您的程式庫。</span><span class="sxs-lookup"><span data-stu-id="75e62-108">If you've developed a library that targets the .NET Standard, your library can be consumed by any .NET implementation that supports the .NET Standard.</span></span> <span data-ttu-id="75e62-109">這表示您無法事先知道特定類型是否可序列化;您只能判斷它在執行時間是否可序列化。</span><span class="sxs-lookup"><span data-stu-id="75e62-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="75e62-110">您可以藉由抓取 <xref:System.Type.IsSerializable> 代表物件類型之物件的屬性值，判斷物件是否可在執行時間序列化 <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="75e62-110">You can determine whether an object is serializable at run time by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="75e62-111">下列範例提供一個實作為。</span><span class="sxs-lookup"><span data-stu-id="75e62-111">The following example provides one implementation.</span></span> <span data-ttu-id="75e62-112">它會定義 `IsSerializable(Object)` 擴充方法，以指出是否 <xref:System.Object> 可以序列化任何實例。</span><span class="sxs-lookup"><span data-stu-id="75e62-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="75e62-113">接著，您可以將任何物件傳遞至方法，以判斷它是否可以在目前的 .NET 執行中進行序列化和還原序列化，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="75e62-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a><span data-ttu-id="75e62-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75e62-114">See also</span></span>

- [<span data-ttu-id="75e62-115">二進位序列化</span><span class="sxs-lookup"><span data-stu-id="75e62-115">Binary serialization</span></span>](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
