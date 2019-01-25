---
title: HOW TO：從服務端點匯出中繼資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b6c4dfd0-f270-43ec-961a-e16eb6af2f2c
ms.openlocfilehash: 86ad062f7b7ee3dd2927f8b5b103adfd719a963d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529984"
---
# <a name="how-to-export-metadata-from-service-endpoints"></a><span data-ttu-id="20909-102">HOW TO：從服務端點匯出中繼資料</span><span class="sxs-lookup"><span data-stu-id="20909-102">How to: Export Metadata from Service Endpoints</span></span>
<span data-ttu-id="20909-103">本主題說明如何從服務端點匯出中繼資料。</span><span class="sxs-lookup"><span data-stu-id="20909-103">This topic explains how to export metadata from service endpoints.</span></span>  
  
### <a name="to-export-metadata-from-service-endpoints"></a><span data-ttu-id="20909-104">從服務端點匯出中繼資料</span><span class="sxs-lookup"><span data-stu-id="20909-104">To export metadata from service endpoints</span></span>  
  
1.  <span data-ttu-id="20909-105">建立新的 Visual Studio 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="20909-105">Create a new Visual Studio Console App Project.</span></span> <span data-ttu-id="20909-106">將下列步驟所示的程式碼加入至 main() 方法內所產生的 Program.cs 檔案中。</span><span class="sxs-lookup"><span data-stu-id="20909-106">Add the code shown in the following steps in the generated Program.cs file within the main() method.</span></span>  
  
2.  <span data-ttu-id="20909-107">建立 <xref:System.ServiceModel.Description.WsdlExporter>。</span><span class="sxs-lookup"><span data-stu-id="20909-107">Create a <xref:System.ServiceModel.Description.WsdlExporter>.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3.  <span data-ttu-id="20909-108">將 <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> 屬性設定為 <xref:System.ServiceModel.Description.PolicyVersion> 列舉的其中一個值。</span><span class="sxs-lookup"><span data-stu-id="20909-108">Set the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to one of the values from the <xref:System.ServiceModel.Description.PolicyVersion> enumeration.</span></span> <span data-ttu-id="20909-109">這個範例將值設定為對應至 WS-Policy 1.5 的 <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>。</span><span class="sxs-lookup"><span data-stu-id="20909-109">This sample sets the value to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> which corresponds to WS-Policy 1.5.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4.  <span data-ttu-id="20909-110">建立 <xref:System.ServiceModel.Description.ServiceEndpoint> 物件的陣列。</span><span class="sxs-lookup"><span data-stu-id="20909-110">Create an array of <xref:System.ServiceModel.Description.ServiceEndpoint> objects.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5.  <span data-ttu-id="20909-111">匯出各個服務端點的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="20909-111">Export metadata for each service endpoint.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6.  <span data-ttu-id="20909-112">檢查以確定在匯出處理期間沒有發生錯誤，並擷取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="20909-112">Check to make sure no errors occurred during the export process and retrieve the metadata.</span></span>  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7.  <span data-ttu-id="20909-113">現在您可以呼叫 <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> 方法，以使用中繼資料 (例如寫入至檔案)。</span><span class="sxs-lookup"><span data-stu-id="20909-113">You can now use the metadata, such as write it to a file by calling the <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20909-114">範例</span><span class="sxs-lookup"><span data-stu-id="20909-114">Example</span></span>  
 <span data-ttu-id="20909-115">以下是這個範例的完整程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="20909-115">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="20909-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="20909-116">Compiling the Code</span></span>  
 <span data-ttu-id="20909-117">編譯 Program.cs 時，請參考 System.ServiceModel.dll。</span><span class="sxs-lookup"><span data-stu-id="20909-117">When compiling Program.cs reference System.ServiceModel.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20909-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20909-118">See also</span></span>
- [<span data-ttu-id="20909-119">中繼資料架構概觀</span><span class="sxs-lookup"><span data-stu-id="20909-119">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [<span data-ttu-id="20909-120">使用中繼資料</span><span class="sxs-lookup"><span data-stu-id="20909-120">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [<span data-ttu-id="20909-121">端點：位址、 繫結和合約</span><span class="sxs-lookup"><span data-stu-id="20909-121">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
