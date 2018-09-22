---
title: 如何判斷是否可序列化的.NET Standard 物件
description: 示範如何判斷在執行階段是否可序列化的.NET Standard 的類型。
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 196e99ab1f1a0baae53c6a1dc295b135e36fbfe0
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46580456"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="850d8-103">如何判斷是否可序列化的.NET Standard 物件</span><span class="sxs-lookup"><span data-stu-id="850d8-103">How to determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="850d8-104">.NET Standard 是定義的類型和成員必須要有特定的.NET 實作符合標準的該版本上的規格。</span><span class="sxs-lookup"><span data-stu-id="850d8-104">The .NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="850d8-105">不過，.NET Standard 並未定義是否可序列化類型。</span><span class="sxs-lookup"><span data-stu-id="850d8-105">However, the .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="850d8-106">.NET Standard 程式庫中定義的類型未標示有<xref:System.SerializableAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="850d8-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="850d8-107">相反地，.NET 特定的實作，例如.NET Framework 和.NET Core，可用來判斷特定的型別是否可序列化。 </span><span class="sxs-lookup"><span data-stu-id="850d8-107">Instead, specific .NET implementations, such as the .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span> 

<span data-ttu-id="850d8-108">如果您已開發目標的.NET Standard 程式庫，您的程式庫可供任何支援.NET Standard 的.NET 實作。</span><span class="sxs-lookup"><span data-stu-id="850d8-108">If you've developed a library that targets the .NET Standard, your library can be consumed by any .NET implementation that supports the .NET Standard.</span></span> <span data-ttu-id="850d8-109">這表示，您無法事先知道特定的型別是否可序列化;您只可以判斷它是否可序列化在執行階段。</span><span class="sxs-lookup"><span data-stu-id="850d8-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="850d8-110">您可以判斷物件是否在執行階段可序列化所擷取的值<xref:System.Type.IsSerializable>屬性<xref:System.Type>物件，表示該物件的型別。</span><span class="sxs-lookup"><span data-stu-id="850d8-110">You can determine whether an object is serializable at runtime by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="850d8-111">下列範例提供一個實作。</span><span class="sxs-lookup"><span data-stu-id="850d8-111">The following example provides one implementation.</span></span> <span data-ttu-id="850d8-112">它會定義`IsSerializable(Object)`擴充方法，指出是否有任何<xref:System.Object>可以序列化執行個體。</span><span class="sxs-lookup"><span data-stu-id="850d8-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="850d8-113">然後，您就可以傳遞任何物件至方法，以判斷它是否可以序列化和還原序列化目前的.NET 實作，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="850d8-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a><span data-ttu-id="850d8-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="850d8-114">See also</span></span>

- [<span data-ttu-id="850d8-115">二進位序列化</span><span class="sxs-lookup"><span data-stu-id="850d8-115">Binary serialization</span></span>](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
