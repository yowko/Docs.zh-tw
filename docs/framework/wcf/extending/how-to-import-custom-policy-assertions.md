---
title: 作法：匯入自訂原則判斷提示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f41d787-accb-4a10-bfc6-a807671d1581
ms.openlocfilehash: 627b68d707dbedfaf6a291f2ab22dbc9a4f60835
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363852"
---
# <a name="how-to-import-custom-policy-assertions"></a>作法：匯入自訂原則判斷提示
原則判斷提示描述服務端點的功能與需求。  用戶端應用程式可使用服務中繼資料中的原則判斷提示，來設定用戶端繫結或自訂服務端點的服務合約。  
  
 您可以藉由實作 <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> 介面並將該物件傳遞至中繼資料系統，或藉由在應用程式組態檔中註冊實作類型，來匯入自訂原則判斷提示。  <xref:System.ServiceModel.Description.IPolicyImportExtension>介面的實現必須提供無參數的函式。  
  
### <a name="to-import-custom-policy-assertions"></a>若要匯入自訂原則判斷提示  
  
1. 在類別上實作 <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> 介面。 請參閱下列程序。  
  
2. 透過以下方式插入自訂原則匯入工具：  
  
3. 使用組態檔。 請參閱下列程序。  
  
4. 使用設定檔案搭配[System.servicemodel 中繼資料公用程式工具 (Svcutil .exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。 請參閱下列程序。  
  
5. 以程式設計方式插入原則匯入工具。 請參閱下列程序。  
  
### <a name="to-implement-the-systemservicemodeldescriptionipolicyimportextension-interface-on-any-class"></a>實作任何類別上的 System.ServiceModel.Description.IPolicyImportExtension 介面  
  
1. 在 <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> 方法中，對於每個您感興趣的原則主體，在傳遞至方法的 <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> 物件上呼叫適當的方法 (視您要的判斷提示範圍而定) 來尋找您要匯入的原則判斷提示。 下列程式碼範例說明如何使用 <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> 方法找到自訂原則判斷提示，並用一個步驟將它從集合中移除。 如果您使用移除方法找到並移除判斷提示，就不必執行步驟 4。  
  
     [!code-csharp[CustomPolicySample#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyimporter.cs#9)]
     [!code-vb[CustomPolicySample#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyimporter.vb#9)]  
  
2. 處理原則判斷提示。 請注意，原則系統不會正規化巢狀原則和 `wsp:optional`。 您必須在原則匯入延伸實作中處理這些建構函式。  
  
3. 對支援原則判斷提示所指定能力或需求的繫結程序或合約執行自訂。 判斷提示通常會指出繫結需要特別的組態或特定的繫結項目。 透過存取 <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=nameWithType> 屬性進行這些修改。 其他判斷提示需要您修改合約。  您可以使用 <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=nameWithType> 屬性存取和修改合約。  請注意，您的原則匯入工具可以為同樣的繫結和合約呼叫多次，但如果無法匯入原則替代選項，則會以不同的原則替代。 您的程式碼應回復到此行為。  
  
4. 從判斷提示集合移除自訂原則判斷提示。 如果您沒有移除判斷提示 Windows Communication Foundation (WCF) 會假設原則匯入不成功, 而且不會匯入相關聯的系結。 如果您使用 <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> 方法找到自訂原則判斷提示，並用一個步驟將它從集合中移除，就不必執行這個步驟。  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-a-configuration-file"></a>若要使用組態檔將自訂原則匯入工具插入中繼資料系統  
  
1. 將匯入工具類型新增`<extensions>`至用戶端設定檔中[ \<policyImporters >](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)元素內的元素。  
  
     [!code-xml[CustomPolicySample#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.exe.config#7)]   
  
2. 在用戶端應用程式中，使用 <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> 或 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> 來解析中繼資料，匯入工具會自動叫用。  
  
     [!code-csharp[CustomPolicySample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.cs#10)]
     [!code-vb[CustomPolicySample#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.vb#10)]  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-svcutilexe"></a>若要使用 Svcutil.exe 將自訂原則匯入工具插入中繼資料系統  
  
1. 將匯入工具類型新增`<extensions>`至 Svcutil 設定檔中[ \<policyImporters >](../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)元素內的元素。 您也可以使用 `/svcutilConfig` 選項指示 Svcutil.exe 載入在不同組態檔中註冊的原則匯入工具。  
  
2. 使用[System.servicemodel 中繼資料公用程式工具 (Svcutil)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來匯入中繼資料, 並自動叫用匯入工具。  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-programmatically"></a>若要以程式設計方式將自訂原則匯入工具插入中繼資料系統  
  
1. 先將匯入工具新增至 <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=nameWithType> 屬性 (例如，如果您目前使用的是 <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>)，再匯入中繼資料。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- [擴充中繼資料系統](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)
