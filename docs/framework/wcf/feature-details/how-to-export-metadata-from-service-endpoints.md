---
title: HOW TO：從服務端點匯出中繼資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b6c4dfd0-f270-43ec-961a-e16eb6af2f2c
ms.openlocfilehash: 9235498956f53d69b3024d1db023f3eb0908d2aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-export-metadata-from-service-endpoints"></a>HOW TO：從服務端點匯出中繼資料
本主題說明如何從服務端點匯出中繼資料。  
  
### <a name="to-export-metadata-from-service-endpoints"></a>從服務端點匯出中繼資料  
  
1.  建立新的 Visual Studio 主控台應用程式專案。 將下列步驟所示的程式碼加入至 main() 方法內所產生的 Program.cs 檔案中。  
  
2.  建立 <xref:System.ServiceModel.Description.WsdlExporter>。  
  
     [!code-csharp[S_UEWsdlExporter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#1)]
     [!code-vb[S_UEWsdlExporter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#1)]  
  
3.  將 <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> 屬性設定為 <xref:System.ServiceModel.Description.PolicyVersion> 列舉的其中一個值。 這個範例將值設定為對應至 WS-Policy 1.5 的 <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>。  
  
     [!code-csharp[S_UEWsdlExporter#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#2)]
     [!code-vb[S_UEWsdlExporter#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#2)]  
  
4.  建立 <xref:System.ServiceModel.Description.ServiceEndpoint> 物件的陣列。  
  
     [!code-csharp[S_UEWsdlExporter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#3)]
     [!code-vb[S_UEWsdlExporter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#3)]  
  
5.  匯出各個服務端點的中繼資料。  
  
     [!code-csharp[S_UEWsdlExporter#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#4)]
     [!code-vb[S_UEWsdlExporter#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#4)]  
  
6.  檢查以確定在匯出處理期間沒有發生錯誤，並擷取中繼資料。  
  
     [!code-csharp[S_UEWsdlExporter#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#5)]
     [!code-vb[S_UEWsdlExporter#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#5)]  
  
7.  現在您可以呼叫 <xref:System.ServiceModel.Description.MetadataSet.WriteTo%28System.Xml.XmlWriter%29> 方法，以使用中繼資料 (例如寫入至檔案)。  
  
## <a name="example"></a>範例  
 以下是這個範例的完整程式碼清單。  
  
 [!code-csharp[S_UEWsdlExporter#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_uewsdlexporter/cs/program.cs#0)]
 [!code-vb[S_UEWsdlExporter#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_uewsdlexporter/vb/program.vb#0)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 編譯 Program.cs 時，請參考 System.ServiceModel.dll。  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料架構概觀](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [使用中繼資料](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [端點：位址、繫結和合約](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
