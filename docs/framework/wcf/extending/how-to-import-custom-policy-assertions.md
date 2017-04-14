---
title: "HOW TO：匯入自訂原則判斷提示 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1f41d787-accb-4a10-bfc6-a807671d1581
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# HOW TO：匯入自訂原則判斷提示
原則判斷提示描述服務端點的功能與需求。  用戶端應用程式可使用服務中繼資料中的原則判斷提示，來設定用戶端繫結或自訂服務端點的服務合約。  
  
 藉由實作匯入自訂原則判斷提示<xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=fullName>介面並將該物件傳遞至中繼資料系統，或註冊實作類型應用程式組態檔中。  實作<xref:System.ServiceModel.Description.IPolicyImportExtension>介面必須提供預設建構函式。  
  
### <a name="to-import-custom-policy-assertions"></a>若要匯入自訂原則判斷提示  
  
1.  實作<xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=fullName>類別的介面。 請參閱下列程序。  
  
2.  透過以下方式插入自訂原則匯入工具：  
  
3.  使用組態檔。 請參閱下列程序。  
  
4.  使用組態檔與[ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。 請參閱下列程序。  
  
5.  以程式設計方式插入原則匯入工具。 請參閱下列程序。  
  
### <a name="to-implement-the-systemservicemodeldescriptionipolicyimportextension-interface-on-any-class"></a>實作任何類別上的 System.ServiceModel.Description.IPolicyImportExtension 介面  
  
1.  在<xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=fullName>方法，對於每個原則主體，您有興趣，尋找您想要藉由呼叫適當的方法 （視您要的判斷提示的範圍） 匯入的原則判斷提示上<xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=fullName>物件傳遞給方法。 下列程式碼範例示範如何使用<xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=fullName>方法找到自訂原則判斷提示，並將它移除，從集合中一個步驟。 如果您使用移除方法找到並移除判斷提示，就不必執行步驟 4。  
  
     [!code-csharp[CustomPolicySample#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyimporter.cs#9)]
     [!code-vb[CustomPolicySample#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyimporter.vb#9)]  
  
2.  處理原則判斷提示。 請注意，原則系統不會正規化巢狀原則和 `wsp:optional`。 您必須在原則匯入延伸實作中處理這些建構函式。  
  
3.  對支援原則判斷提示所指定能力或需求的繫結或合約執行自訂。 判斷提示通常會指出繫結需要特別的組態或特定的繫結項目。 藉由存取進行這些修改<xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=fullName>屬性。 其他判斷提示需要您修改合約。  您可以存取和修改合約使用<xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=fullName>屬性。  請注意，您的原則匯入工具可以為同樣的繫結和合約呼叫多次，但如果無法匯入原則替代選項，則會以不同的原則替代。 您的程式碼應回復到此行為。  
  
4.  從判斷提示集合移除自訂原則判斷提示。 如果您沒有移除判斷提示，[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 會假設原則匯入不成功，而不會匯入有關聯的繫結。 如果您使用<xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=fullName>方法找到自訂原則判斷提示，並將它移除，從集合中沒有執行此步驟的其中一個步驟。  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-a-configuration-file"></a>若要使用組態檔將自訂原則匯入工具插入中繼資料系統  
  
1.  新增匯入工具型別的`<extensions>`項目內[ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)用戶端組態檔中的項目。  
  
     [!code[CustomPolicySample#7](../../../../samples/snippets/common/VS_Snippets_CFX/custompolicysample/common/client.exe.config#7)]
     [!code-csharp[CustomPolicySample#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.exe.config#7)]
     [!code-vb[CustomPolicySample#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.exe.config#7)]  
  
2.  在用戶端應用程式中，使用<xref:System.ServiceModel.Description.MetadataResolver?displayProperty=fullName>或<xref:System.ServiceModel.Description.WsdlImporter?displayProperty=fullName>解析中繼資料匯入工具會自動叫用。  
  
     [!code-csharp[CustomPolicySample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.cs#10)]
     [!code-vb[CustomPolicySample#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.vb#10)]  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-svcutilexe"></a>若要使用 Svcutil.exe 將自訂原則匯入工具插入中繼資料系統  
  
1.  新增匯入工具型別的`<extensions>`項目內[ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md) Svcutil.exe.config 組態檔中的項目。 您也可以使用 `/svcutilConfig` 選項指示 Svcutil.exe 載入在不同組態檔中註冊的原則匯入工具。  
  
2.  使用[ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)匯入中繼資料和匯入工具會自動叫用。  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-programmatically"></a>若要以程式設計方式將自訂原則匯入工具插入中繼資料系統  
  
1.  加入要匯入工具<xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=fullName>屬性 (例如，如果您使用<xref:System.ServiceModel.Description.WsdlImporter?displayProperty=fullName>) 再匯入中繼資料。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=fullName>   
 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=fullName>   
 <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=fullName>   
 [擴充中繼資料系統](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)