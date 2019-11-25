---
title: 使用序列化繫結器
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: bfce2a14c8757250c520919c8ff2a4d7048a9d5c
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138657"
---
# <a name="usage-of-serialization-binder"></a><span data-ttu-id="55ce7-102">使用序列化繫結器</span><span class="sxs-lookup"><span data-stu-id="55ce7-102">Usage of Serialization Binder</span></span>
<span data-ttu-id="55ce7-103">此範例示範如何使用 <xref:System.Runtime.Serialization.SerializationBinder> 變更序列化時一般類型的版本。</span><span class="sxs-lookup"><span data-stu-id="55ce7-103">This sample shows how to use the <xref:System.Runtime.Serialization.SerializationBinder> to change the version of a generic type when it is serialized.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="55ce7-104">示範</span><span class="sxs-lookup"><span data-stu-id="55ce7-104">Demonstrates</span></span>  
 <span data-ttu-id="55ce7-105"><xref:System.Runtime.Serialization.SerializationBinder>、 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span><span class="sxs-lookup"><span data-stu-id="55ce7-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="55ce7-106">討論</span><span class="sxs-lookup"><span data-stu-id="55ce7-106">Discussion</span></span>  
 <span data-ttu-id="55ce7-107">這個範例示範兩個以不同 .NET Framework 版本為目標的實體如何使用二進位格式器和序列化系結器來進行通訊。</span><span class="sxs-lookup"><span data-stu-id="55ce7-107">This sample shows how two entities that are targeting different versions of the .NET Framework can communicate using the binary formatter and the serialization binder.</span></span>  
  
<span data-ttu-id="55ce7-108">這個範例是使用 .NET 遠端處理所開發的。</span><span class="sxs-lookup"><span data-stu-id="55ce7-108">This sample was developed using .NET Remoting.</span></span> <span data-ttu-id="55ce7-109">其包含以 .NET Framework 4 為目標的伺服器，其可執行具有泛型型別的合約，以及兩個不同的用戶端，一個目標為 .NET Framework 2.0，另一個目標為 .NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="55ce7-109">It consists of a server targeting .NET Framework 4, which implements a contract with generic types, and two different clients, one targeting .NET Framework 2.0 and another targeting .NET Framework 4.</span></span>  
  
 <span data-ttu-id="55ce7-110">伺服器會將 <xref:System.Runtime.Serialization.SerializationBinder> 附加到 Binary Formatter 以便能夠根據序列化變更型別的版本，因此，兩個用戶端都可以正確還原序列化這些型別。</span><span class="sxs-lookup"><span data-stu-id="55ce7-110">The server attaches a <xref:System.Runtime.Serialization.SerializationBinder> to the binary formatter to be able to change the version of the types accordingly on serialization, so both clients can deserialize those types properly.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="55ce7-111">若要設定、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="55ce7-111">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="55ce7-112">若要執行用戶端，請以滑鼠右鍵按一下方案 [SBGenericsVTS （6個專案）]，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="55ce7-112">To execute the client, right-click the solution, SBGenericsVTS (6 projects) and then select **Properties**.</span></span>  
  
2. <span data-ttu-id="55ce7-113">在 [**通用屬性**] 中，選取 [**啟始專案**]，然後選取 [**多個啟始專案**]。</span><span class="sxs-lookup"><span data-stu-id="55ce7-113">In **Common Properties**, select **Startup Project**, then select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="55ce7-114">依序選取 [ **Server** first]、[ **Client20** ] 和 [ **Client40**]。</span><span class="sxs-lookup"><span data-stu-id="55ce7-114">Select **Server** first, then **Client20** and then **Client40**.</span></span> <span data-ttu-id="55ce7-115">選取這三個專案的 [**啟動**] 動作，並將其餘設定保留為 [**無**]。</span><span class="sxs-lookup"><span data-stu-id="55ce7-115">Select the **Start** action to these three projects and leave the rest set to **None**.</span></span>  
  
4. <span data-ttu-id="55ce7-116">按一下 **[確定]** ，然後按 F5 執行範例。</span><span class="sxs-lookup"><span data-stu-id="55ce7-116">Click **OK** and then press F5 to run the sample.</span></span>
