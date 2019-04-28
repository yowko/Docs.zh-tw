---
title: 資料合約已知型別
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], known types
- KnownTypeAttribute [WCF]
- KnownTypes [WCF]
ms.assetid: 1a0baea1-27b7-470d-9136-5bbad86c4337
ms.openlocfilehash: bedf35544454a32ff13856a072779cd70723e989
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857164"
---
# <a name="data-contract-known-types"></a>資料合約已知型別
<xref:System.Runtime.Serialization.KnownTypeAttribute> 類別可讓您預先指定在還原序列化期間應該納入考量的型別。 如需實用範例，請參閱 [Known Types](../../../../docs/framework/wcf/samples/known-types.md) 範例。  
  
 一般來說，當您在用戶端與服務之間傳送參數並傳回值時，兩邊的端點都會共用要傳送之資料的所有資料合約。 但是，這種現象在下列情況中不會出現：  
  
- 傳送的資料合約是由預期的資料合約衍生而來。 如需詳細資訊，請參閱中的繼承的小節[資料合約等價](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md))。 在此情況下，所傳送資料的資料合約與接收的端點所預期的資料合約不會一樣。  
  
- 要傳送的資訊宣告型別是一種介面，而不是類別、結構或列舉。 因此，您無法預先得知實際傳送了哪種可實作介面的型別，也因此接收的端點無法預先判斷已傳送資料的資料合約。  
  
- 要傳送的資訊宣告型別為 <xref:System.Object>。 由於每種型別都繼承自 <xref:System.Object>，而且您無法預先得知實際傳送的型別，因此接收的端點無法預先判斷已傳送資料的資料合約。 這是特殊案例的第一個項目：每個資料合約衍生自預設值，會針對產生的空白資料合約<xref:System.Object>。  
  
- 有些型別 (包括 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別) 的成員隸屬於先前三大類別的其中一個類別。 例如， <xref:System.Collections.Hashtable> 會透過 <xref:System.Object> 將實際物件儲存到雜湊資料表中。 在序列化這些型別時，接收的一方無法預先判斷這些成員的資料合約。  
  
## <a name="the-knowntypeattribute-class"></a>KnownTypeAttribute 類別  
 當資料抵達接收的結束點時，WCF 執行階段會嘗試將資料還原序列化的 common language runtime (CLR) 類型執行個體。 還原系列化作業所產生的型別，首先會經由檢查傳入訊息來判斷訊息內容所符合的資料合約來加以選定。 接著，還原序列化引擎會嘗試尋找可實作資料合約 (相容於訊息內容) 的 CLR 型別。 在此處理序中，我們會將還原序列化引擎所允許的候選型別集合稱為還原序列化程式的「已知型別」集合。  
  
 讓還原序列化引擎識別型別的一種方式，就是使用 <xref:System.Runtime.Serialization.KnownTypeAttribute>。 屬性無法套用至個別資料成員，只能套用至整個資料合約型別。 屬性會套用至可以是類別或結構的「 *外部型別* 」(Outer Type)。 在屬性最基本的用途當中，套用屬性會將型別指定為「已知型別」。 這樣一來，每當外部型別的物件或是透過其成員參照的任何物件進行還原序列化，已知型別就會變成已知型別集合的一部分。 超過一個以上的 <xref:System.Runtime.Serialization.KnownTypeAttribute> 屬性可以套用至相同型別中。  
  
## <a name="known-types-and-primitives"></a>已知型別與基本型別  
 基本型別，以及被視為基本型別的特性型別 (例如， <xref:System.DateTime> 和 <xref:System.Xml.XmlElement>) 將一律具有「已知」狀態，而且一律不需要透過此機制來新增。 但是，您需要明確地新增基本型別陣列。 大部分的集合都會被視為與陣列相等 (非泛型集合將被視為與 <xref:System.Object>陣列相等)。 如需使用基本型別、基本型別陣列，與基本型別集合的範例，請參閱範例 4。  
  
> [!NOTE]
>  與其他基本型別不同的是， <xref:System.DateTimeOffset> 結構預設並不是已知型別，所以必須手動新增至已知型別清單中。  
  
## <a name="examples"></a>範例  
 下列範例說明使用中的 <xref:System.Runtime.Serialization.KnownTypeAttribute> 類別。  
  
#### <a name="example-1"></a>範例 1  
 具有繼承關係的類別共有三個。  
  
 [!code-csharp[C_KnownTypeAttribute#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#1)]
 [!code-vb[C_KnownTypeAttribute#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#1)]  
  
 如果 `CompanyLogo` 成員已設為 `ShapeOfLogo` 或 `CircleType` 物件，由於還原序列化引擎無法識別任何具有資料合約名稱 "Circle" 或 "Triangle" 的型別，您將可以序列化下列 `TriangleType` 類別，但是無法加以還原序列化。  
  
 [!code-csharp[C_KnownTypeAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#2)]
 [!code-vb[C_KnownTypeAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#2)]  
  
 下列程式碼說明如何正確撰寫 `CompanyLogo` 型別。  
  
 [!code-csharp[C_KnownTypeAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#3)]
 [!code-vb[C_KnownTypeAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#3)]  
  
 每次在還原序列化外部型別 `CompanyLogo2` 時，還原序列化引擎能夠識別 `CircleType` 和 `TriangleType` ，因此能夠為 "Circle" 和 "Triangle" 資料找尋相符的型別。  
  
#### <a name="example-2"></a>範例 2  
 在下列範例中，即使 `CustomerTypeA` 和 `CustomerTypeB` 同時具有 `Customer` 資料合約，每當還原序列化 `CustomerTypeB` 時，還是會建立 `PurchaseOrder` 執行個體，因為還原序列化引擎只能識別 `CustomerTypeB` 。  
  
 [!code-csharp[C_KnownTypeAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#4)]
 [!code-vb[C_KnownTypeAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#4)]  
  
#### <a name="example-3"></a>範例 3  
 在下列範例中， <xref:System.Collections.Hashtable> 會將其內容當成 <xref:System.Object>儲存在內部。 為了成功還原序列化雜湊資料表，還原序列化引擎必須能夠識別可在該處發生的可能型別集合。 在此情況下，我們預先知道只有 `Book` 和 `Magazine` 物件會儲存在 `Catalog`中，因此會透過 <xref:System.Runtime.Serialization.KnownTypeAttribute> 屬性來加以新增。  
  
 [!code-csharp[C_KnownTypeAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#5)]
 [!code-vb[C_KnownTypeAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#5)]  
  
#### <a name="example-4"></a>範例 4  
 在下列範例中，資料合約會儲存數字與用來執行數字的運算式。 `Numbers` 資料成員可以是整數、整數陣列，或是包含整數的 <xref:System.Collections.Generic.List%601> 。  
  
> [!CAUTION]
>  如果使用 SVCUTIL.EXE 來產生 WCF Proxy，這將只能在用戶端上運作。 SVCUTIL.EXE 會從服務擷取中繼資料，包括所有已知的型別。 如果沒有這項資訊，用戶端將無法還原序列化型別。  
  
 [!code-csharp[C_KnownTypeAttribute#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#6)]
 [!code-vb[C_KnownTypeAttribute#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#6)]  
  
 下列為應用程式程式碼。  
  
 [!code-csharp[C_KnownTypeAttribute#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#7)]
 [!code-vb[C_KnownTypeAttribute#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#7)]  
  
## <a name="known-types-inheritance-and-interfaces"></a>已知型別、繼承，與介面  
 當已知型別透過 `KnownTypeAttribute` 屬性關聯至特定型別時，已知型別同時已經和該型別的所有衍生型別產生關聯。 例如，請參閱下列程式碼。  
  
 [!code-csharp[C_KnownTypeAttribute#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#8)]
 [!code-vb[C_KnownTypeAttribute#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#8)]  
  
 `DoubleDrawing` 類別不會要求 `KnownTypeAttribute` 屬性使用 `Square` 欄位中的 `Circle` 和 `AdditionalShape` ，因為基底類別 (`Drawing`) 已經套用了這些屬性。  
  
 已知型別只可和類別與結構，而不能與介面產生關聯。  
  
## <a name="known-types-using-open-generic-methods"></a>使用開放式泛型方法的已知型別  
 您可能需要將泛型型別新增為已知型別。 但是，開放式泛型型別無法當成 `KnownTypeAttribute` 屬性的參數來傳送。  
  
 使用的替代機制，即可解決此問題：撰寫一個方法，傳回一份要加入至已知型別集合的型別。 接著，因為某些限制因素，可將方法名稱指定為 `KnownTypeAttribute` 屬性的字串引數。  
  
 方法必須存在於套用 `KnownTypeAttribute` 屬性的型別上、必須是靜態的、絕對不得接受任何參數，而且必須傳回可指派給 <xref:System.Collections.IEnumerable> 之 <xref:System.Type>的物件。  
  
 您無法將 `KnownTypeAttribute` 屬性與方法名稱結合，也無法將 `KnownTypeAttribute` 屬性與相同型別上的實際型別結合。 此外，您無法將一個以上包含方法名稱的 `KnownTypeAttribute` 套用至相同型別中。  
  
 請參閱下列類別。  
  
 [!code-csharp[C_KnownTypeAttribute#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#9)]
 [!code-vb[C_KnownTypeAttribute#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#9)]  
  
 `theDrawing` 欄位包含泛型類別 `ColorDrawing` 和泛型類別 `BlackAndWhiteDrawing`的執行個體，兩者都繼承自泛型類別 `Drawing`。 一般來說，兩者必須同時新增至已知型別中，但是下列不是有效的屬性語法。  
  
```csharp  
// Invalid syntax for attributes:  
// [KnownType(typeof(ColorDrawing<T>))]  
// [KnownType(typeof(BlackAndWhiteDrawing<T>))]  
```  
  
```vb  
' Invalid syntax for attributes:  
' <KnownType(GetType(ColorDrawing(Of T))), _  
' KnownType(GetType(BlackAndWhiteDrawing(Of T)))>  
```  
  
 因此，您必須建立方法來傳回這些型別。 下列程式碼將接著說明撰寫此型別的正確方式。  
  
 [!code-csharp[C_KnownTypeAttribute#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_knowntypeattribute/cs/source.cs#10)]
 [!code-vb[C_KnownTypeAttribute#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_knowntypeattribute/vb/source.vb#10)]  
  
## <a name="additional-ways-to-add-known-types"></a>新增已知型別的其他方式  
 另外，您可以透過組態檔來新增已知型別。 當您不能控制需要已知型別進行適當還原序列化，例如當使用協力廠商型別程式庫與 Windows Communication Foundation (WCF) 的型別時，這非常有用。  
  
 下列組態檔示範如何在組態檔中指定已知的型別。  
  
 `<configuration>`  
  
 `<system.runtime.serialization>`  
  
 `<dataContractSerializer>`  
  
 `<declaredTypes>`  
  
 `<add type="MyCompany.Library.Shape,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL">`  
  
 `<knownType type="MyCompany.Library.Circle,`  
  
 `MyAssembly, Version=2.0.0.0, Culture=neutral,`  
  
 `PublicKeyToken=XXXXXX, processorArchitecture=MSIL"/>`  
  
 `</add>`  
  
 `</declaredTypes>`  
  
 `</dataContractSerializer>`  
  
 `</system.runtime.serialization>`  
  
 `</configuration>`  
  
 在先前的組態檔中，會宣告稱為 `MyCompany.Library.Shape` 的資料合約型別，而讓 `MyCompany.Library.Circle` 做為已知的型別。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.KnownTypeAttribute>
- <xref:System.Collections.Hashtable>
- <xref:System.Object>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>
- [已知類型](../../../../docs/framework/wcf/samples/known-types.md)
- [資料合約等價](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [設計服務合約](../../../../docs/framework/wcf/designing-service-contracts.md)
