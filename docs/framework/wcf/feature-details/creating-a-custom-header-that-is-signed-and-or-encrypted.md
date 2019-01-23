---
title: 建立自訂標頭已簽署和-或已加密
ms.date: 03/30/2017
ms.assetid: e8668b37-c79f-4714-9de5-afcb88b9ff02
ms.openlocfilehash: 0f8f86bcb5494cd502d14aff1cf3c4cdf4f8dd33
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494817"
---
# <a name="creating-a-custom-header-that-is-signed-and-or-encrypted"></a>建立自訂標頭已簽署和-或已加密
使用 WCF 用戶端來呼叫非 WCF 服務時，有時候必須使用自訂 SOAP 標頭。 WCF 具有一個規範化 Bug，這個 Bug 會讓已簽署和加密的自訂標頭無法使用非 WCF 服務。 這個問題是預設 XML 命名空間的規範化錯誤所造成。 只有當您使用已簽署和 (或) 加密的自訂標頭來呼叫非 WCF 服務時，才會發生這個問題。  當此服務收到包含已簽署和 (或) 加密之自訂標頭的訊息時，它無法驗證簽章。 這種解決方法會避免規範化 Bug、允許與非 WCF 服務互通，但是無法防止與 WCF 服務互通。  
  
## <a name="defining-the-custom-header"></a>定義自訂標頭  
 自訂標頭的定義方式如下：定義訊息合約，然後使用 <xref:System.ServiceModel.MessageHeaderAttribute> 屬性來標記您想要當做標頭傳送的成員。 若要解決規範化 Bug，您必須確定 XML 序列化程式會使用前置詞而非預設命名空間宣告來宣告自訂標頭的命名空間。 下列程式碼將示範如何使用正確的命名空間宣告來定義將當做訊息標頭使用的資料型別。  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("svcutil", "3.0.4506.648")]  
[System.SerializableAttribute()]  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.ComponentModel.DesignerCategoryAttribute("code")]  
[System.Xml.Serialization.XmlTypeAttribute(AnonymousType=true, Namespace="http://www.example.org/getMessage/")]  
public partial class msgHeaderElement  
{  
   // Define the XML namespace and force it to use an ‘h’ prefix  
    [System.Xml.Serialization.XmlNamespaceDeclarations]  
    public System.Xml.Serialization.XmlSerializerNamespaces _xsns = new System.Xml.Serialization.XmlSerializerNamespaces(new System.Xml.XmlQualifiedName[] { new System.Xml.XmlQualifiedName("h", "http://www.example.org/getMessage/") });  
  
    private string msgHeaderInputField;  
  [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified, Order=0)]  
    public string msgHeaderInput  
    {  
        get  
        {  
            return this.msgHeaderInputField;  
        }  
        set  
        {  
            this.msgHeaderInputField = value;  
        }  
    }  
}  
```  
  
 這段程式碼會宣告名為 `msgHeaderElement` 的新型別，而這個型別將使用 XML 序列化程式來序列化。 序列化這個型別的執行個體時，它將使用 ‘h’ 前置詞來定義命名空間，因而解決規範化 Bug。  然後，訊息合約會定義 `msgHeaderElement` 的執行個體，並且使用 <xref:System.ServiceModel.MessageHeaderAttribute> 屬性來標記它，如下列範例所示。  
  
```  
[MessageContract]  
public  class MyMessageContract  
{  
   // other message contents...  
   [MessageHeader(ProductionLevel=ProtectionLevel.EncryptAndSign)]  
   public msgHeaderElement;  
   // other message contents...  
}  
```  
  
## <a name="see-also"></a>另請參閱
- [預設訊息合約](../../../../docs/framework/wcf/samples/default-message-contract.md)
- [訊息合約](../../../../docs/framework/wcf/samples/message-contracts.md)
- [使用訊息合約](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)
