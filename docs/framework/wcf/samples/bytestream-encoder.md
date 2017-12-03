---
title: "ByteStream 編碼器"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e674a8ab-f79a-4a93-b984-54b34392dafc
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7663e0c0073110c0df2e3ece20c240af46a61e92
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="bytestream-encoder"></a><span data-ttu-id="324e6-102">ByteStream 編碼器</span><span class="sxs-lookup"><span data-stu-id="324e6-102">ByteStream Encoder</span></span>
<span data-ttu-id="324e6-103">這個範例示範如何建立 `ByteStreamHttpBinding`，也就是示範位元組資料流編碼器功能的 <xref:System.ServiceModel.Channels.Binding>。</span><span class="sxs-lookup"><span data-stu-id="324e6-103">This sample demonstrates how to create a `ByteStreamHttpBinding`, a <xref:System.ServiceModel.Channels.Binding> that demonstrates the functionality of the byte stream encoder.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="324e6-104">討論</span><span class="sxs-lookup"><span data-stu-id="324e6-104">Discussion</span></span>  
 <span data-ttu-id="324e6-105">這個範例示範如何使用標準的繫結項目 <xref:System.ServiceModel.Channels.Binding> 和 <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> 建立標準的 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="324e6-105">This sample demonstrates how to create a standard <xref:System.ServiceModel.Channels.Binding> using the standard binding elements <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span> <span data-ttu-id="324e6-106">這個範例示範如何使用位元組資料流編碼器上傳和下載影像。</span><span class="sxs-lookup"><span data-stu-id="324e6-106">This sample shows how to use the byte stream encoder to upload and download an image.</span></span> <span data-ttu-id="324e6-107">位元組資料流編碼器功能僅支援 HTTP 傳輸，並不支援可靠的訊息處理 (Reliable Messaging) 或安全性這類功能。</span><span class="sxs-lookup"><span data-stu-id="324e6-107">The byte stream encoder feature only supports the HTTP transport and it does not support features such as reliable messaging or security.</span></span> <span data-ttu-id="324e6-108">唯一支援的 <xref:System.ServiceModel.Channels.MessageVersion> 是 <xref:System.ServiceModel.Channels.MessageVersion.None%2A>。</span><span class="sxs-lookup"><span data-stu-id="324e6-108">The only <xref:System.ServiceModel.Channels.MessageVersion> supported is <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="324e6-109">如果您是在 [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] 或 [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)] 中執行這個範例，請確定您是以更高的權限執行 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="324e6-109">If you are running this sample in [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] or [!INCLUDE[win7_client_firstref](../../../../includes/win7-client-firstref-md.md)], ensure that you are running [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] with elevated privileges.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="324e6-110">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="324e6-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="324e6-111">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="324e6-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="324e6-112">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="324e6-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="324e6-113">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="324e6-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\ByteStreamEncoder`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="324e6-114">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="324e6-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="324e6-115">在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中開啟 [ByteStreamHttpBinding.sln] 檔案。</span><span class="sxs-lookup"><span data-stu-id="324e6-115">Open the ByteStreamHttpBinding.sln file in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="324e6-116">啟動 ByteStreamHttpBindingServer 專案的新執行個體，以滑鼠右鍵按一下 [方案總管] 中的專案，然後選取**偵錯**，然後**開始新執行個體**從內容功能表。</span><span class="sxs-lookup"><span data-stu-id="324e6-116">Start a new instance of the ByteStreamHttpBindingServer project by right-clicking the project in the Solution Explorer and selecting **Debug**, and then **Start new instance** from the context menu.</span></span>  
  
3.  <span data-ttu-id="324e6-117">啟動 ByteStreamHttpBindingClient 專案的新執行個體，以滑鼠右鍵按一下 [方案總管] 中的專案，然後選取**偵錯**，**開始新執行個體**從內容功能表。</span><span class="sxs-lookup"><span data-stu-id="324e6-117">Start a new instance of the ByteStreamHttpBindingClient project by right-clicking the project in the Solution Explorer and selecting **Debug**, **Start new instance** from the context menu.</span></span>
