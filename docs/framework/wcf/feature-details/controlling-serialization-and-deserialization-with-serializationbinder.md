---
title: "以 SerializationBinder 控制序列化與還原序列化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1c3180d62824f94e27e02c80e09fdf32252f0a23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a><span data-ttu-id="98cc0-102">以 SerializationBinder 控制序列化與還原序列化</span><span class="sxs-lookup"><span data-stu-id="98cc0-102">Controlling Serialization and Deserialization with SerializationBinder</span></span>
<span data-ttu-id="98cc0-103">在序列化期間，格式器會傳輸在建立正確型別和版本之物件執行個體時的必要資訊。</span><span class="sxs-lookup"><span data-stu-id="98cc0-103">During serialization, a formatter transmits the information required to create an instance of an object of the correct type and version.</span></span> <span data-ttu-id="98cc0-104">這項資訊通常包含物件的完整型別名稱和組件名稱。</span><span class="sxs-lookup"><span data-stu-id="98cc0-104">This information generally includes the full type name and assembly name of the object.</span></span> <span data-ttu-id="98cc0-105">根據預設，還原序列化會使用這項資訊建立完全相同物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="98cc0-105">By default, deserialization uses this information to create an instance of an identical object.</span></span> <span data-ttu-id="98cc0-106">某些使用者可能因為執行還原序列化的電腦上不存在原始類別、原始類別已在組件之間移動，或是伺服器和用戶端上需要不同版本的類別，而需要控制要序列化和還原序列化的類別。</span><span class="sxs-lookup"><span data-stu-id="98cc0-106">Some users may need to control which class to serialize and deserialize, either because the original class may not exist on the machine performing deserialization, the original class has moved between assemblies, or a different version of the class is required on the server and client.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="98cc0-107">[序列化繫結器的使用方式](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)。</span><span class="sxs-lookup"><span data-stu-id="98cc0-107"> [Usage of Serialization Binder](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="98cc0-108">此功能只有在使用 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 或 <xref:System.Runtime.Serialization.NetDataContractSerializer> 時才能使用。</span><span class="sxs-lookup"><span data-stu-id="98cc0-108">This functionality is only available when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or the <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span>  
  
## <a name="using-serializationbinder"></a><span data-ttu-id="98cc0-109">使用 SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="98cc0-109">Using SerializationBinder</span></span>  
 <span data-ttu-id="98cc0-110"><xref:System.Runtime.Serialization.SerializationBinder> 是抽象類別，用來控制序列化和還原序列化期間使用的實際型別。</span><span class="sxs-lookup"><span data-stu-id="98cc0-110"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span> <span data-ttu-id="98cc0-111">若要控制序列化和還原序列化期間使用的型別，衍生自<xref:System.Runtime.Serialization.SerializationBinder>並覆寫<xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A>System.String、 System.String)?qualifyHint=False & autoUpgrade = True 和<xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A>System.String)？qualifyHint = False & autoUpgrade = True 的方法。</span><span class="sxs-lookup"><span data-stu-id="98cc0-111">To control the types used during serialization and deserialization, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String, System.String)?qualifyHint=False&autoUpgrade=True and <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String)?qualifyHint=False&autoUpgrade=True methods.</span></span> <span data-ttu-id="98cc0-112"><xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String、 System.String)?qualifyHint=False & autoUpgrade = True 的方法會採用<xref:System.Type>，並傳回組件和類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="98cc0-112">The <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String, System.String)?qualifyHint=False&autoUpgrade=True method takes a <xref:System.Type> and returns an assembly and type name.</span></span> <span data-ttu-id="98cc0-113"><xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String)?qualifyHint=False & autoUpgrade = True 的方法會採用組件和型別名稱，然後傳回<xref:System.Type>。</span><span class="sxs-lookup"><span data-stu-id="98cc0-113">The <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String)?qualifyHint=False&autoUpgrade=True method takes an assembly and type name and returns a <xref:System.Type>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98cc0-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98cc0-114">See Also</span></span>  
 [<span data-ttu-id="98cc0-115">序列化和還原序列化</span><span class="sxs-lookup"><span data-stu-id="98cc0-115">Serialization and Deserialization</span></span>](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)  
 [<span data-ttu-id="98cc0-116">序列化繫結器的使用方式</span><span class="sxs-lookup"><span data-stu-id="98cc0-116">Usage of Serialization Binder</span></span>](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
