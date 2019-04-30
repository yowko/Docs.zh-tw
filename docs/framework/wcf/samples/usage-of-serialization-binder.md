---
title: 使用序列化繫結器
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: 47a1974386927316ea9230ec27cf647d7245c44a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007587"
---
# <a name="usage-of-serialization-binder"></a><span data-ttu-id="cf5c6-102">使用序列化繫結器</span><span class="sxs-lookup"><span data-stu-id="cf5c6-102">Usage of Serialization Binder</span></span>
<span data-ttu-id="cf5c6-103">此範例示範如何使用 <xref:System.Runtime.Serialization.SerializationBinder> 變更序列化時一般類型的版本。</span><span class="sxs-lookup"><span data-stu-id="cf5c6-103">This sample shows how to use the <xref:System.Runtime.Serialization.SerializationBinder> to change the version of a generic type when it is serialized.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="cf5c6-104">示範</span><span class="sxs-lookup"><span data-stu-id="cf5c6-104">Demonstrates</span></span>  
 <span data-ttu-id="cf5c6-105"><xref:System.Runtime.Serialization.SerializationBinder>、 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span><span class="sxs-lookup"><span data-stu-id="cf5c6-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="cf5c6-106">討論</span><span class="sxs-lookup"><span data-stu-id="cf5c6-106">Discussion</span></span>  
 <span data-ttu-id="cf5c6-107">此範例示範目標為不同版本之 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的兩個實體如何使用 Binary Formatter 和序列化繫結器進行通訊。</span><span class="sxs-lookup"><span data-stu-id="cf5c6-107">This sample shows how two entities that are targeting different versions of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] can communicate using the binary formatter and the serialization binder.</span></span>  
  
 <span data-ttu-id="cf5c6-108">此範例的開發已經使用 .NET Remoting 完成。</span><span class="sxs-lookup"><span data-stu-id="cf5c6-108">The development of this sample has been done using .NET Remoting.</span></span> <span data-ttu-id="cf5c6-109">此範例由目標為 [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] 且實作具有一般類型之合約的一個伺服器，以及兩個不同的用戶端 (一個目標為 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] 而另一個目標為 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]) 所組成。</span><span class="sxs-lookup"><span data-stu-id="cf5c6-109">The sample consists of a server targeting [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], which implements a contract with generic types, and two different clients, one targeting [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] and another targeting [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].</span></span>  
  
 <span data-ttu-id="cf5c6-110">伺服器會將 <xref:System.Runtime.Serialization.SerializationBinder> 附加到 Binary Formatter 以便能夠根據序列化變更型別的版本，因此，兩個用戶端都可以正確還原序列化這些型別。</span><span class="sxs-lookup"><span data-stu-id="cf5c6-110">The server attaches a <xref:System.Runtime.Serialization.SerializationBinder> to the binary formatter to be able to change the version of the types accordingly on serialization, so both clients can deserialize those types properly.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cf5c6-111">若要設定、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="cf5c6-111">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="cf5c6-112">若要執行用戶端，以滑鼠右鍵按一下 sbgenericsvts （6 個專案），然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="cf5c6-112">To execute the client, right-click the solution, SBGenericsVTS (6 projects) and then select **Properties**.</span></span>  
  
2. <span data-ttu-id="cf5c6-113">在 **通用屬性**，選取**啟始專案**，然後選取**多個啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="cf5c6-113">In **Common Properties**, select **Startup Project**, then select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="cf5c6-114">選取 **伺服器**第一，然後**Client20** ，然後**Client40**。</span><span class="sxs-lookup"><span data-stu-id="cf5c6-114">Select **Server** first, then **Client20** and then **Client40**.</span></span> <span data-ttu-id="cf5c6-115">選取 **開始**這三個動作專案，並保留其餘設定為**無**。</span><span class="sxs-lookup"><span data-stu-id="cf5c6-115">Select the **Start** action to these three projects and leave the rest set to **None**.</span></span>  
  
4. <span data-ttu-id="cf5c6-116">按一下 **確定**，然後按 F5 執行範例。</span><span class="sxs-lookup"><span data-stu-id="cf5c6-116">Click **OK** and then press F5 to run the sample.</span></span>
