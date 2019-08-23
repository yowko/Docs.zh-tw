---
title: 作法：設定 ProtectionLevel 屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
ms.openlocfilehash: 222fda180923cdc7b0d7b7ab413c151c69add259
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950971"
---
# <a name="how-to-set-the-protectionlevel-property"></a>作法：設定 ProtectionLevel 屬性
您可以套用適當的屬性 (Attribute) 並設定屬性 (Property)，藉此設定保護層級。 您可以設定服務層級的保護，以影響每一個訊息的所有部分，或是從方法到訊息部分，設定越發細微的保護層級。 如需有關屬性的`ProtectionLevel`詳細資訊, 請參閱[瞭解保護層級](../../../docs/framework/wcf/understanding-protection-level.md)。  
  
> [!NOTE]
> 您只能在程式碼中設定保護層級，而不能在組態中設定。  
  
### <a name="to-sign-all-messages-for-a-service"></a>簽署服務的所有訊息  
  
1. 建立服務的介面。  
  
2. 將 <xref:System.ServiceModel.ServiceContractAttribute> 屬性 (Attribute) 套用至服務，並且將 <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> 屬性 (Property) 設為 <xref:System.Net.Security.ProtectionLevel.Sign>，如以下程式碼中所示 (預設層級為 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>)。  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a>簽署作業的所有訊息部分  
  
1. 建立服務的介面，並且將 <xref:System.ServiceModel.ServiceContractAttribute> 屬性套用至介面。  
  
2. 將方法宣告加入至介面。  
  
3. 將 <xref:System.ServiceModel.OperationContractAttribute> 屬性 (Attribute) 套用至方法，並且將 <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> 屬性 (Property) 設為 <xref:System.Net.Security.ProtectionLevel.Sign>，如以下程式碼中所示。  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a>保護錯誤訊息  
 在服務上擲回的例外狀況可以當成 SOAP 錯誤傳送至用戶端。 如需建立強型別錯誤的詳細資訊, 請參閱[指定和處理合約和服務中的錯誤](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)和[如何:宣告服務合約](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md)中的錯誤。  
  
#### <a name="to-protect-a-fault-message"></a>保護錯誤訊息  
  
1. 建立表示錯誤訊息的類型。 以下範例將建立名為 `MathFault` 的類別，其中包含兩個欄位。  
  
2. 將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至類型，並且將 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性套用至應序列化的每一個欄位，如以下程式碼所示。  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3. 在傳回錯誤的介面中，將 <xref:System.ServiceModel.FaultContractAttribute> 屬性套用至傳回錯誤的方法，並且將 `detailType` 參數設為錯誤類別的類型。  
  
4. 同時，在建構函式中，將 <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> 屬性設為 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>，如以下程式碼所示。  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a>保護訊息部分  
 使用訊息合約保護訊息的部分。 如需訊息合約的詳細資訊, 請參閱[使用訊息合約](../../../docs/framework/wcf/feature-details/using-message-contracts.md)。  
  
#### <a name="to-protect-a-message-body"></a>保護訊息本文  
  
1. 建立表示訊息的類型。 以下範例將建立 `Company` 類別，其中包含兩個欄位 `CompanyName` 和 `CompanyID`。  
  
2. 將 <xref:System.ServiceModel.MessageContractAttribute> 屬性 (Attribute) 套用至類別，並且將 <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> 屬性 (Property) 設為 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>。  
  
3. 將 <xref:System.ServiceModel.MessageHeaderAttribute> 屬性 (Attribute) 套用以訊息標頭表示的欄位，並且將 `ProtectionLevel` 屬性 (Property) 設為 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>。  
  
4. 將套用`ProtectionLevel` <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>至任何將表示為訊息主體一部分的欄位, 並將屬性設定為, 如下列範例所示。 <xref:System.ServiceModel.MessageBodyMemberAttribute>  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a>範例  
 以下範例會在服務中的不同位置，設定數個屬性 (Attribute) 類別的 `ProtectionLevel` 屬性 (Property)。  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 以下範例示範編譯範例程式碼所需的命名空間。  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- [了解保護層級](../../../docs/framework/wcf/understanding-protection-level.md)
