---
title: 本機通道
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 87e140395ac2fb5702d8655cf970da8a60c991ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144503"
---
# <a name="local-channel"></a><span data-ttu-id="ebd37-102">本機通道</span><span class="sxs-lookup"><span data-stu-id="ebd37-102">Local Channel</span></span>
<span data-ttu-id="ebd37-103">本地通道是用於同一應用程式域內通信的 Windows 通信基礎 （WCF） 傳輸通道。</span><span class="sxs-lookup"><span data-stu-id="ebd37-103">Local Channel is a Windows Communication Foundation (WCF) transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="ebd37-104">這個通道在用戶端和服務於相同應用程式定義域中執行，而必須避免一般 WCF 通道堆疊的負荷 (序列化和還原序列化訊息) 時相當實用。</span><span class="sxs-lookup"><span data-stu-id="ebd37-104">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="ebd37-105">示範</span><span class="sxs-lookup"><span data-stu-id="ebd37-105">Demonstrates</span></span>  
 <span data-ttu-id="ebd37-106">本機通道</span><span class="sxs-lookup"><span data-stu-id="ebd37-106">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="ebd37-107">討論區</span><span class="sxs-lookup"><span data-stu-id="ebd37-107">Discussion</span></span>  
 <span data-ttu-id="ebd37-108">此範例包含二個專案檔：</span><span class="sxs-lookup"><span data-stu-id="ebd37-108">The sample consists of two project files:</span></span>  
  
- <span data-ttu-id="ebd37-109">**本地通道**：當前應用程式域中本地通道的程式設計表示形式。</span><span class="sxs-lookup"><span data-stu-id="ebd37-109">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="ebd37-110">在此專案中，傳送的元件會將訊息放入記憶體內部佇列，而接收元件則會取消訊息佇列並接收該訊息。</span><span class="sxs-lookup"><span data-stu-id="ebd37-110">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
- <span data-ttu-id="ebd37-111">**用戶端和服務**：此專案在主控台應用程式中託管服務，然後運行用戶端以從同一應用程式域中調用該服務。</span><span class="sxs-lookup"><span data-stu-id="ebd37-111">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="ebd37-112">本機通道的設計在於同時略過通道堆疊和序列化程序，以加快速度。</span><span class="sxs-lookup"><span data-stu-id="ebd37-112">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="ebd37-113">本機傳輸通道是使用佇列實作，以便將服務呼叫從用戶端傳輸至服務，以及將值傳回到用戶端。</span><span class="sxs-lookup"><span data-stu-id="ebd37-113">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="ebd37-114">這個範例不會序列化參數和傳回值，而會複製物件。</span><span class="sxs-lookup"><span data-stu-id="ebd37-114">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ebd37-115">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="ebd37-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ebd37-116">建置及執行 LocalChannel 方案。</span><span class="sxs-lookup"><span data-stu-id="ebd37-116">Build and run the LocalChannel solution.</span></span>  
  
2. <span data-ttu-id="ebd37-117">服務主機會啟動，而用戶端會使用本機通道呼叫服務。</span><span class="sxs-lookup"><span data-stu-id="ebd37-117">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="ebd37-118">主控台視窗隨即出現，並顯示服務呼叫的結果。</span><span class="sxs-lookup"><span data-stu-id="ebd37-118">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ebd37-119">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="ebd37-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ebd37-120">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="ebd37-120">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ebd37-121">如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。</span><span class="sxs-lookup"><span data-stu-id="ebd37-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ebd37-122">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="ebd37-122">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
