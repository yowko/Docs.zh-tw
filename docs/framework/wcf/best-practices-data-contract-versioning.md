---
title: 最佳做法：資料合約版本控制
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- service contracts
- best practices [WCF], data contract versioning
- Windows Communication Foundation, data contracts
ms.assetid: bf0ab338-4d36-4e12-8002-8ebfdeb346cb
ms.openlocfilehash: cf3ae6f47f63c545edf3d65804daa049d4541788
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59334922"
---
# <a name="best-practices-data-contract-versioning"></a>最佳做法：資料合約版本控制
本主題會列出最佳做法以建立可隨時間輕鬆改進的資料合約。 如需資料合約的詳細資訊，請參閱中的主題[Using Data Contracts](../../../docs/framework/wcf/feature-details/using-data-contracts.md)。  
  
## <a name="note-on-schema-validation"></a>結構描述驗證注意事項  
 在討論資料合約版本控制，請務必請注意，匯出由 Windows Communication Foundation (WCF) 的資料合約結構描述沒有任何版本控制支援，除了根據預設會標示為選擇性項目。  
  
 這表示即使最常見的版本設定案例 (例如新增資料成員)，也無法以與指定結構描述完全整合的方式來實作。 較新版的資料合約 (例如具有新的資料成員) 不會使用舊的結構描述來驗證。  
  
 然而，有許多案例並不需要嚴格的結構描述相容性。 許多 Web 的服務平台，包括使用 ASP.NET 建立的 WCF 和 XML Web service 請勿執行預設的結構描述驗證，因此可容許結構描述未描述的額外項目。 當使用此類平台時，許多版本設定案例都更容易實作。  
  
 因此，有兩組資料合約版本設定指導方針：一組適用於嚴格結構描述驗證很重要的案例，另一組適用於不重要的案例。  
  
## <a name="versioning-when-schema-validation-is-required"></a>需要結構描述驗證時的版本設定  
 如果在所有方向中 (新至舊以及舊至新)，都需要嚴格結構描述驗證，資料合約應視為固定不變的。 如果需要版本設定，應使用不同的名稱或命名空間來建立新的資料合約，而且使用此資料型別的服務合約應依此進行版本設定。  
  
 例如，名為 `PoProcessing` 的訂單處理服務合約，以及採用符合 `PostPurchaseOrder` 資料合約之參數的 `PurchaseOrder` 作業。 如果 `PurchaseOrder` 合約必須變更，您必須建立新的資料合約，也就是包含變更的 `PurchaseOrder2`。 然後您必須在服務合約層處理版本設定。 例如，藉由建立採用 `PostPurchaseOrder2` 參數的 `PurchaseOrder2` 作業，或藉由建立 `PoProcessing2` 服務合約，其中 `PostPurchaseOrder` 作業是採用 `PurchaseOrder2` 資料合約。  
  
 請注意，其他資料合約所參照之資料合約中的變更也會延伸至服務模型層。 例如，在前面的案例中，`PurchaseOrder` 資料合約不需要變更。 然而，它包含 `Customer` 資料合約的資料成員，其中包含需要變更之 `Address` 資料合約的資料成員。 在該案例中，您將需要建立含有所需變更的 `Address2` 資料合約、包含 `Customer2` 資料成員的 `Address2` 資料合約，以及包含 `PurchaseOrder2` 資料成員的 `Customer2` 資料合約。 如同在前面的案例中，服務合約也必須進行版本設定。  
  
 雖然在這些範例中，名稱已變更 (附加一個 "2")，但建議您將新的命名空間加上版本號碼或日期，來變更命名空間而非名稱。 例如，`http://schemas.contoso.com/2005/05/21/PurchaseOrder` 資料合約會變更為 `http://schemas.contoso.com/2005/10/14/PurchaseOrder` 資料合約。  
  
 如需詳細資訊，請參閱 < 最佳作法：[服務版本設定](../../../docs/framework/wcf/service-versioning.md)。  
  
 雖然有時候，您必須為應用程式傳送的訊息，保證具有嚴格結構描述相容性，但不能依賴傳入訊息來達到嚴格的結構描述相容性。 此案例具有一項危險性，就是傳入訊息可能會包含一些無關的資料。 沒有直接關聯的值儲存，並傳回由 WCF 因此造成傳送訊息的結構描述無效。 如果要避免這個問題，應關閉往返功能。 執行這項作業的方法有兩種。  
  
-   請勿在您任何的型別上實作 <xref:System.Runtime.Serialization.IExtensibleDataObject> 介面。  
  
-   將 <xref:System.ServiceModel.ServiceBehaviorAttribute> 屬性設定為 <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A>，以套用 `true` 屬性至您的服務合約。  
  
 如需往返的詳細資訊，請參閱[向前相容資料合約](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)。  
  
## <a name="versioning-when-schema-validation-is-not-required"></a>不需要結構描述驗證時的版本設定  
 嚴格結構描述相容性很少有需要。 許多平台都會容許結構描述未描述的額外項目。 只要容許這種情況，完整的功能中所述[資料合約版本控制](../../../docs/framework/wcf/feature-details/data-contract-versioning.md)並[向前相容資料合約](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)可用。 建議使用下列指導方針。  
  
 有些指導方針必須確實遵守，才能對預期收到舊版本之處傳送新版本的型別，或對預期收到新版本之處傳送舊的版本。 其他的指導方針並非絕對必要，但在此處會列出，因為它們可能會受到未來結構描述版本設定的影響。  
  
1. 請勿嘗試依型別繼承對資料合約進行版本設定。 如果要建立較新版本，請變更現有型別上的資料合約或建立不相關的新型別。  
  
2. 如果繼承沒有用來做為版本設定機制，並遵循特定規則，便允許搭配使用繼承和資料合約。 如果型別衍生自特定的基底型別，在未來版本中請勿讓它衍生自不同的基底型別 (除非它有相同的資料合約)。 這種情形有一個例外狀況：只有在不包含名稱與繼承中其他型別之任何可能版本中的其他成員相同的資料成員時，您才可以將型別插入資料合約類型和其基底型別之間的繼承中。 一般來說，在相同繼承階層之不同層級使用名稱相同的資料成員，會導致嚴重的版本設定問題，應加以避免。  
  
3. 從資料合約的第一個版本開始時，請永遠實作 <xref:System.Runtime.Serialization.IExtensibleDataObject> 以啟用往返。 如需詳細資訊，請參閱[向前相容資料合約](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)。 如果您已發行型別的一或多個版本，而沒有實作這個介面，請在型別的下一個版本中實作它。  
  
4. 在較新的版本中，請勿變更資料合約名稱或命名空間。 如果變更做為資料合約基礎之型別的名稱或命名空間，請使用適當的機制以確定保留資料合約名稱和命名空間，例如 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> 的 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性。 如需有關命名的詳細資訊，請參閱 < [Data Contract Names](../../../docs/framework/wcf/feature-details/data-contract-names.md)。  
  
5. 在較新的版本中，請勿變更任何資料成員的名稱。 如果變更做為資料成員基礎的欄位、屬性或事件的名稱，請使用 `Name` 的 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性來保留現有的資料成員名稱。  
  
6. 在較新的版本中，請勿變更做為資料成員基礎之任何欄位、屬性或事件的型別，讓該資料成員的結果資料合約改變。 請記住，如果是為了判斷預期資料合約的目的，介面型別等於 <xref:System.Object>。  
  
7. 在較新的版本中，請勿藉由調整 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> 屬性的 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性，來變更現有資料成員的順序。  
  
8. 在較新的版本中，可以新增新的資料成員。 它們應永遠遵循下列規則：  
  
    1.  <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 屬性應永遠保持為 `false` 的預設值。  
  
    2.  如果無法接受成員為 `null` 預設值或零，而成員未出現在傳入的資料流中，就應使用 <xref:System.Runtime.Serialization.OnDeserializingAttribute> 以提供合理的預設值來提供回呼方法。 如需回呼的詳細資訊，請參閱[版本相容序列化回呼](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)。  
  
    3.  <xref:System.Runtime.Serialization.DataMemberAttribute.Order?displayProperty=nameWithType>屬性應該用來確保所有新加入的資料成員都會出現在現有的資料成員之後。 執行此動作的建議的方法如下所示：資料成員中的資料合約的第一個版本都不應該有其`Order`屬性集。 資料合約第二個版本中加入的所有資料成員都不應將其 `Order` 屬性設定為 2。 資料合約第三個版本中加入的所有資料成員都不應將其 `Order` 屬性設定為 3，以此類推。 您可以將一個以上的資料成員設定為相同的 `Order` 號碼。  
  
9. 即使 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 屬性保持為在舊版中 `false` 的預設屬性，也請不要在新版中移除資料成員。  
  
10. 請勿在版本之間變更任何現有資料成員上的 `IsRequired` 屬性。  
  
11. 對於所需要的資料成員 (其中 `IsRequired` 為 `true`)，請勿在版本之間變更 `EmitDefaultValue` 屬性。  
  
12. 請勿嘗試建立分支版本階層。 也就是說，在不同版本之間，應該永遠有至少一個方向的路徑，只使用這些指導方針所允許的變更。  
  
     例如，如果 Person 資料合約的第 1 版只包含 Name 資料成員，您就不應建立只新增 Age 成員的合約第 2a 版，以及只新增 Address 成員的第 2b 版。 從 2a 到 2b 會包含移除 Age 及新增 Address；而另一個方向則會需要移除 Address 及新增 Age。 這些指導方針不允許移除成員。  
  
13. 您通常不應該在新版的應用程式中建立現有資料合約類型的新子類型。 同樣地，您不應建立新的資料合約，用於取代宣告為物件或介面型別的資料成員。 只有在您知道可以將新型別新增至舊應用程式之所有執行個體的已知型別清單時，才允許建立這些新的類別。 例如，在您應用程式的第 1 版中，可能有 LibraryItem 資料合約類型以及 Book 和 Newspaper 資料合約子類型。 然後 LibraryItem 將會有包含 Book 和 Newspaper 的已知型別清單。 假設您現在要在第 2 版中新增 Magazine 型別，做為 LibraryItem 的子型別。 如果您將 Magazine 執行個體從第 2 版傳送至第 1 版，在已知型別的清單中會找不到 Magazine 資料合約，而且會擲回例外狀況。  
  
14. 您不應在版本之間新增或移除列舉成員。 您也不應重新命名列舉成員，除非您使用 `EnumMemberAttribute` 屬性 (Attribute) 上的 Name 屬性 (Property) 讓它們的名稱在資料合約模型中保持相同。  
  
15. 集合是可互換的資料合約模型中所述[集合 Types in Data Contracts](../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md)。 這可允許更大程度的彈性。 然而，請確定您沒有在版本之間以不可互換的方式不慎變更集合型別。 例如，請勿從非自訂的集合 (也就是沒有 `CollectionDataContractAttribute` 屬性) 變更為自訂的集合，或從自訂的集合變更為非自訂的集合。 此外，請勿在版本之間變更 `CollectionDataContractAttribute` 上的屬性。 唯一允許的變更是，如果基礎集合型別的名稱或命名空間已變更，而您需要讓其資料合約名稱和命名空間和舊版本中的相同，則可新增 Name 或 Namespace 屬性。  
  
 當情況特殊時，可以放心略過此處列出的一些指導方針。 在違背指導方針之前，請確定您完全瞭解其中的序列化、還原序列化以及結構描述機制。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>
- <xref:System.Runtime.Serialization.ExtensionDataObject>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- [使用資料合約](../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [資料合約版本控制](../../../docs/framework/wcf/feature-details/data-contract-versioning.md)
- [資料合約名稱](../../../docs/framework/wcf/feature-details/data-contract-names.md)
- [向前相容資料合約](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)
- [版本相容序列化回呼](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
