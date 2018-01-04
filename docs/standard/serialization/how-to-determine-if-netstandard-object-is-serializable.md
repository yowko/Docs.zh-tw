---
title: "如何： 判斷是否可序列化的.NET 標準物件"
description: "示範如何判斷在執行階段是否可序列化的.NET 標準的類型。"
ms.custom: 
ms.date: 10/20/2017
ms.prod: .net
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7c44e350ad4e561f03bf6c598172058a0a9ca41e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="b3f26-103">如何： 判斷是否可序列化的.NET 標準物件</span><span class="sxs-lookup"><span data-stu-id="b3f26-103">How to: Determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="b3f26-104">.NET 標準是定義的類型和成員必須要有特定的.NET 實作符合標準的該版本上的規格。</span><span class="sxs-lookup"><span data-stu-id="b3f26-104">The .NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="b3f26-105">不過，.NET 標準並未定義是否可序列化類型。</span><span class="sxs-lookup"><span data-stu-id="b3f26-105">However, the .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="b3f26-106">.NET 的標準程式庫中定義的類型未標示有<xref:System.SerializableAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="b3f26-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="b3f26-107">相反地，.NET 特定的實作，例如.NET Framework 和.NET 核心，可用來判斷特定的型別是否可序列化。</span><span class="sxs-lookup"><span data-stu-id="b3f26-107">Instead, specific .NET implementations, such as the .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span> 

<span data-ttu-id="b3f26-108">如果您已開發目標的.NET 標準程式庫，您的程式庫可供任何支援.NET 標準的.NET 實作。</span><span class="sxs-lookup"><span data-stu-id="b3f26-108">If you've developed a library that targets the .NET Standard, your library can be consumed by any .NET implementation that supports the .NET Standard.</span></span> <span data-ttu-id="b3f26-109">這表示，您無法事先知道特定的型別是否可序列化。您只可以判斷它是否可序列化在執行階段。</span><span class="sxs-lookup"><span data-stu-id="b3f26-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="b3f26-110">您可以判斷物件是否可序列化，在執行階段所擷取的值<xref:System.Type.IsSerializable>屬性<xref:System.Type>物件，表示該物件的類型。</span><span class="sxs-lookup"><span data-stu-id="b3f26-110">You can determine whether an object is serializable at runtime by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="b3f26-111">下列範例提供一個實作。</span><span class="sxs-lookup"><span data-stu-id="b3f26-111">The following example provides one implementation.</span></span> <span data-ttu-id="b3f26-112">它會定義`IsSerializable(Object)`擴充方法，指出是否有任何<xref:System.Object>可以序列化執行個體。</span><span class="sxs-lookup"><span data-stu-id="b3f26-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="b3f26-113">然後，您可以傳遞任何物件至方法，以判斷它是否可以序列化和還原序列化於目前的.NET 實作，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b3f26-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

# <a name="see-also"></a><span data-ttu-id="b3f26-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3f26-114">See also</span></span>

<span data-ttu-id="b3f26-115">[二進位序列化](binary-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="b3f26-115">[Binary serialization](binary-serialization.md) </span></span>  
<span data-ttu-id="b3f26-116"><xref:System.SerializableAttribute?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b3f26-116"><xref:System.SerializableAttribute?displayProperty=fullName></span></span>    
<xref:System.Type.IsSerializable?displayProperty=nameWithType>   
