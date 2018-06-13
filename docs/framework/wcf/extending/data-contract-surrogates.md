---
title: 資料合約代理
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], surrogates
ms.assetid: 8c31134c-46c5-4ed7-94af-bab0ac0dfce5
ms.openlocfilehash: b06cb45d6075c8de1da973a11e2edec6792df304
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809465"
---
# <a name="data-contract-surrogates"></a>資料合約代理
資料合約*surrogate*是資料合約模型上建置的進階的功能。 這項功能是專為在使用者想要變更型別序列化、還原序列化或投射至中繼資料的方式時，用來自訂和替換型別所設計。 某些可能使用代理的情況包括：尚未指定型別的資料合約、欄位和屬性 (Property) 尚未以 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 (Attribute) 標記，或是使用者希望動態建立結構描述變形時。  
  
 序列化和還原序列化是在使用 <xref:System.Runtime.Serialization.DataContractSerializer> 從 .NET Framework 轉換為適合的格式 (例如 XML) 時，使用資料合約代理完成。 資料合約代理也可以在產生中繼資料表示 (例如 XML 結構描述文件，XSD) 時，用來修改針對型別匯出的中繼資料。 匯入時，程式碼會從中繼資料建立，而代理同樣可以在這種情況下用來自訂產生的程式碼。  
  
## <a name="how-the-surrogate-works"></a>代理的運作方式  
 代理是藉由對應一種型別 (「原始」型別) 到另一種型別 (「代理」型別) 的方式運作。 下列範例示範原始型別 `Inventory` 和新的代理 `InventorySurrogated` 型別。 `Inventory` 型別無法序列化，但是 `InventorySurrogated` 型別可以序列化。  
  
 [!code-csharp[C_IDataContractSurrogate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#1)]  
  
 由於尚未定義這個類別的資料合約，因此請使用資料合約將這個類別轉換成代理類別。 下列範例會顯示代理的類別：  
  
 [!code-csharp[C_IDataContractSurrogate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#2)]  
  
## <a name="implementing-the-idatacontractsurrogate"></a>實作 IDataContractSurrogate  
 若要使用資料合約代理，請實作 <xref:System.Runtime.Serialization.IDataContractSurrogate> 介面。  
  
 下列是每種 <xref:System.Runtime.Serialization.IDataContractSurrogate> 方法的概觀，包括可能的實作。  
  
### <a name="getdatacontracttype"></a>GetDataContractType  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> 方法會將一種型別對應到另一種。 這個方法為序列化、還原序列化、匯入和匯出時所需。  
  
 第一項工作是定義要對應到其他型別的型別。 例如:   
  
 [!code-csharp[C_IDataContractSurrogate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#3)]  
  
-   在序列化過程中，這個方法傳回的對應會接著藉由呼叫 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> 方法，將原始執行個體轉換成代理執行個體。  
  
-   在還原序列化的過程中，這個方法傳回的對應會由序列化程式用來還原序列化為代理型別的執行個體。 接著它會呼叫 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> 將代理執行個體轉換成原始型別的執行個體。  
  
-   在匯出過程中，這個方法傳回的代理型別會加以反映，以便將資料合約用於產生中繼資料。  
  
-   在匯入過程中，初始型別會變更為反映的代理型別，以便將資料合約用於參考支援這類目的。  
  
 <xref:System.Type> 參數屬於要序列化、還原序列化、匯入或匯出的物件型別。 如果代理不處理型別，則 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> 方法必須傳回輸入型別。 否則會傳回適當的代理型別。 如果有數個代理型別存在，則可以在這個方法中定義許多對應。  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> 方法不會針對內建的資料合約基本型別呼叫，例如 <xref:System.Int32> 或 <xref:System.String>。 對於其他型別，例如陣列、使用者定義的型別，以及其他資料結構等，都會呼叫這個方法。  
  
 在之前的範例中，方法會檢查 `type` 參數和 `Inventory` 是否可以比較。 如果可以的話，方法就會將它對應到 `InventorySurrogated`。 無論是呼叫序列化、還原序列化、匯入結構描述或匯出結構描述，都會先呼叫這個函式以判斷型別之間的對應。  
  
### <a name="getobjecttoserialize-method"></a>GetObjectToSerialize 方法  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> 方法會將原始型別執行個體轉換成代理型別執行個體。 這是序列化需要的方法。  
  
 下一個步驟是定義實體資料藉由實作 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> 方法，從原始執行個體對應到代理的方式。 例如:   
  
 [!code-csharp[C_IDataContractSurrogate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#4)]  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> 方法會在序列化物件時呼叫。 這個方法會將資料從原始型別傳輸至代理型別的欄位。 欄位可以直接對應到代理欄位，或是原始資料的管理可以儲存在代理中。 一些可能的用法包括：直接對應欄位、在要儲存到代理欄位中的資料上執行作業，或是將原始型別的 XML 儲存到代理欄位中。  
  
 `targetType` 參數會參考宣告的成員型別。 這個參數是由 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> 方法傳回的代理型別。 序列化程式不會強制傳回的物件必須能夠指派給這個型別。 `obj`參數是要序列化的物件，如有必要將轉換成其代理。 如果代理的物件不會處理該物件的話，這個方法就必須傳回輸入物件。 否則將傳回新的代理物件。 如果物件為 null，則不會呼叫代理。 這個物件內可定義許多不同執行個體的代理對應。  
  
 建立 <xref:System.Runtime.Serialization.DataContractSerializer> 時，您可以指示它保留物件參考  (如需詳細資訊，請參閱[序列化和還原序列化](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)。)只要在其建構函式中將 `preserveObjectReferences` 參數設為 `true`，就能達到這個目的。 在這個情況下，只會呼叫物件的代理一次，因為後續的所有序列化會直接將參考寫入資料流中。 如果 `preserveObjectReferences` 設為 `false`，則會在每次遇到執行個體時呼叫代理。  
  
 如果序列化的執行個體型別與宣告的型別不同，則型別資訊會寫入資料流中 (例如 `xsi:type`)，讓執行個體能夠在另一端還原序列化。 這項程序無論物件是否為代理都會發生。  
  
 上面的範例會將 `Inventory` 執行個體的資料轉換成 `InventorySurrogated` 的資料。 它會檢查物件的型別並且執行必要的管理，以轉換成代理型別。 在這個案例中，`Inventory` 類別的欄位會直接複製到 `InventorySurrogated` 類別的欄位中。  
  
### <a name="getdeserializedobject-method"></a>GetDeserializedObject 方法  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> 方法會將代理型別執行個體轉換成原始型別執行個體。 這是還原序列化所需的程序。  
  
 下一項工作是定義將實體資料從代理執行個體對應到原始執行個體的方式。 例如:   
  
 [!code-csharp[C_IDataContractSurrogate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#5)]  
  
 這個方法只會在物件的還原序列化期間呼叫。 它會為還原序列化提供反向資料對應，也就是從代理型別到原始型別。 與 `GetObjectToSerialize` 方法相似的是，某些可能的用法為直接交換欄位資料、在資料上執行作業，以及儲存 XML 資料。 還原序列化時，由於資料轉換的操作方式不同，因此不一定會從原始型別取得確實的資料值。  
  
 `targetType` 參數會參考宣告的成員型別。 這個參數是由 `GetDataContractType` 方法傳回的代理型別。 `obj`參數是指已還原序列化的物件。 如果物件為代理的話，則可以轉換回原始型別。 如果代理不會處理輸入物件的話，這個方法就會傳回該物件。 否則，在轉換完成之後就會傳回還原的物件。 如果有數個代理型別存在，您可以藉由指示每個型別及其轉換的方式，為每個型別提供從代理到主要型別的資料轉換。  
  
 傳回物件時，會以這個代理傳回的物件更新內部物件表格。 後續任何執行個體的參考都將從物件表格取得代理執行個體。  
  
 之前的範例會將 `InventorySurrogated` 型別的物件轉換回初始型別 `Inventory`。 在這個案例中，資料是從 `InventorySurrogated` 直接傳輸回 `Inventory` 中對應的欄位。 由於沒有資料管理，因此每個成員欄位都會包含與序列化之前相同的值。  
  
### <a name="getcustomdatatoexport-method"></a>GetCustomDataToExport 方法  
 匯出結構描述時，<xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A> 方法是選擇性的。 這個方法是用來將額外的資料或提示插入匯出的結構描述中。 額外的資料可在成員層級或型別層級插入。 例如:   
  
 [!code-csharp[C_IDataContractSurrogate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#6)]  
  
 這個方法 (包含兩個多載) 可以在成員或型別層級將額外的資訊加入中繼資料。 另外還可以加入有關成員為公用或私用的提示，以及會在結構描述的整個匯出和匯入過程中保留的註解。 如果沒有這個方法，這類資訊可能會遺失。 這個方法不會造成插入或刪除成員或型別，而是在其中一個層級中將額外的資料加入至結構描述。  
  
 這個方法為多載，而且可以採用 `Type` (`clrtype` 參數) 或 <xref:System.Reflection.MemberInfo> (`memberInfo` 參數)。 第二個參數固定為 `Type` (`dataContractType` 參數)。 這個方法會針對 `dataContractType` 代理型別的每一個成員和型別呼叫。  
  
 其中任一個多載必須傳回 `null` 或可序列化的物件。 非 null 的物件將做為附註序列化成匯出的結構描述。 若為 `Type` 多載，匯出至結構描述的每個型別會隨著代理類別傳送到這個方法的第一個參數中做為 `dataContractType` 參數。 若為 `MemberInfo` 多載，則匯出至結構描述的每個成員都會傳送其資訊，做為第二個參數中代理型別的 `memberInfo` 參數。  
  
#### <a name="getcustomdatatoexport-method-type-type"></a>GetCustomDataToExport 方法 (Type, Type)  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Type%2CSystem.Type%29?displayProperty=nameWithType> 方法會在針對每一個型別定義匯出結構描述的期間呼叫。 這個方法會在匯出時，將資訊加入至結構描述內的型別。 定義的每個型別都會傳送至這個方法，以判斷是否有任何額外的資訊需要加入結構描述中。  
  
#### <a name="getcustomdatatoexport-method-memberinfo-type"></a>GetCustomDataToExport 方法 (MemberInfo, Type)  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=nameWithType> 會在匯出已匯出的型別中每一個成員時呼叫。 這個函式可讓您自訂匯出時，將加入結構描述中之成員的任何註解。 類別內每一個成員的資訊都會傳送至這個方法，以檢查是否有任何額外的資料需要加入結構描述中。  
  
 上面的範例會搜尋 `dataContractType` 中是否有代理的每個成員。 然後為每個欄位傳回適當的存取修飾詞。 如果沒有這個自訂程序，存取修飾詞的預設值就會是公用。 因此，無論實際的存取限制為何，所有成員在使用匯出的結構描述產生的程式碼中，都會定義為公用。 而沒有使用這個實作時，即使 `numpens` 成員在代理中定義為私用，在匯出的結構描述中仍會是公用。 透過使用這個方法，存取修飾詞在匯出的結構描述中就可以產生為私用。  
  
### <a name="getreferencedtypeonimport-method"></a>GetReferencedTypeOnImport 方法  
 這個方法會將代理的 <xref:System.Type> 對應到原始型別。 這個方法對於結構描述的匯入作業來說是選擇性的。  
  
 當建立匯入結構描述及產生其程式碼的代理時，下一項工作就是將代理執行個體的型別定義為其原始型別。  
  
 如果產生的程式碼需要參考現有的使用者型別，可藉由實作 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> 方法達到這個目的。  
  
 匯入結構描述時，會針對每一個型別宣告呼叫這個方法，以便將代理資料合約對應到型別。 字串參數 `typeName` 和 `typeNamespace` 會定義代理型別的名稱和命名空間。 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> 的傳回值則用來判斷是否需要產生新型別。 這個方法必須傳回有效的型別或 null。 若為有效型別，傳回的型別將用來做為所產生程式碼中的參考型別。 如果傳回 null，則不會參考任何型別，而且必須建立新型別。 如果有數個代理存在，則可以將每個代理型別對應回其初始型別。  
  
 `customData` 參數是原本從 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A> 傳回的物件。 這個 `customData` 會在代理的作者想要在匯入以產生程式碼期間，將額外的資料/提示插入要使用的中繼資料時使用。  
  
### <a name="processimportedtype-method"></a>ProcessImportedType 方法  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.ProcessImportedType%2A> 方法會自訂任何從結構描述匯入作業建立的型別。 這個方法是一個選擇項目。  
  
 當匯入結構描述時，這個方法會允許自訂任何匯入的型別和編譯資訊。 例如:   
  
 [!code-csharp[C_IDataContractSurrogate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#7)]  
  
 在匯入期間，會針對產生的每一個型別呼叫這個方法。 請變更指定的 <xref:System.CodeDom.CodeTypeDeclaration> 或修改 <xref:System.CodeDom.CodeCompileUnit>。 包括變更名稱、成員、屬性 (Attribute) 及 `CodeTypeDeclaration` 的許多其他屬性 (Property)。 藉由處理 `CodeCompileUnit`，就可以修改指示詞、命名空間、參考組件及數個其他項目。  
  
 `CodeTypeDeclaration` 參數包含程式碼 DOM 型別宣告。 `CodeCompileUnit` 參數則允許修改處理程式碼的方式。  若傳回 `null`，會導致捨棄型別宣告。 相反地，若傳回 `CodeTypeDeclaration`，則會保留修改。  
  
 如果在中繼資料匯出期間插入自訂資料，則該資料必須在匯入期間提供給使用者才能使用。 這項自訂資料可以用於程式設計模型提示，或其他註解。 每個 `CodeTypeDeclaration` 和包含如 <xref:System.CodeDom.CodeTypeMember> 屬性之自訂資料的 <xref:System.CodeDom.CodeObject.UserData%2A> 執行個體，都會轉換 (Cast) 成 `IDataContractSurrogate` 型別。  
  
 上面的範例會在匯入的結構描述上執行某些變更。 程式碼會使用代理保留原始型別的私用成員。 匯入結構描述時的預設存取修飾詞為 `public`。 因此除非經過修改，否則代理結構描述的所有成員都會是公用，如本範例中所示。 匯出期間，自訂資料會插入有關哪些成員為私用的中繼資料中。 這個範例會查看自訂資料、檢查存取修飾詞是否為私用，然後藉由設定屬性的方式將適當的成員修改為私用。 如果沒有這項自訂程序，`numpens` 成員就會定義為公用而非私用。  
  
### <a name="getknowncustomdatatypes-method"></a>GetKnownCustomDataTypes 方法  
 這個方法會從結構描述取得定義的自訂資料型別。 這個方法對於結構描述的匯入作業來說是選擇性的。  
  
 這個方法會在結構描述匯出和匯入開始時呼叫。 然後傳回在匯出或匯入的結構描述中使用的自訂資料型別。 這個方法會收到傳遞的 <xref:System.Collections.ObjectModel.Collection%601> (`customDataTypes` 參數)，此為型別的集合。 這個方法應將額外的已知型別加入這個集合中。 必須有已知的自訂資料型別，才能使用 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化和還原序列化自訂資料。 如需詳細資訊，請參閱[資料合約已知型別](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。  
  
## <a name="implementing-a-surrogate"></a>實作代理  
 若要使用資料合約代理，WCF 中的，您必須遵循一些特殊的程序。  
  
### <a name="to-use-a-surrogate-for-serialization-and-deserialization"></a>若要使用代理進行序列化和還原序列化  
 您可以使用 <xref:System.Runtime.Serialization.DataContractSerializer> 搭配代理來執行資料序列化和還原序列化。 <xref:System.Runtime.Serialization.DataContractSerializer> 是由 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> 建立。 代理同樣必須指定。  
  
##### <a name="to-implement-serialization-and-deserialization"></a>若要實作序列化和還原序列化  
  
1.  為服務建立 <xref:System.ServiceModel.ServiceHost> 的執行個體。 如需完整指示，請參閱[基本 WCF 程式設計](../../../../docs/framework/wcf/basic-wcf-programming.md)。  
  
2.  針對所指定服務主機的每一個 <xref:System.ServiceModel.Description.ServiceEndpoint>，尋找其 <xref:System.ServiceModel.Description.OperationDescription>。  
  
3.  搜尋作業行為，判斷是否找到 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> 的執行個體。  
  
4.  如果找到 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> 請將其 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> 屬性設為代理的新執行個體。 如果未找到 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>，則建立新執行個體，並且將新行為的 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> 成員設為代理的新執行個體。  
  
5.  最後，將這個新行為加入目前的作業行為中，如下列範例所示：  
  
     [!code-csharp[C_IDataContractSurrogate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#8)]  
  
### <a name="to-use-a-surrogate-for-metadata-import"></a>若要使用代理進行中繼資料匯入  
 匯入中繼資料如 WSDL 和 XSD 以產生用戶端程式碼時，必須將代理加入負責從 XSD 結構描述 <xref:System.Runtime.Serialization.XsdDataContractImporter> 產生程式碼的元件。 若要執行這項操作，請直接修改用來匯入中繼資料的 <xref:System.ServiceModel.Description.WsdlImporter>。  
  
##### <a name="to-implement-a-surrogate-for-metadata-importation"></a>若要實作代理以匯入中繼資料  
  
1.  使用 <xref:System.ServiceModel.Description.WsdlImporter> 類別匯入中繼資料。  
  
2.  使用 <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> 方法檢查是否已定義 <xref:System.Runtime.Serialization.XsdDataContractImporter>。  
  
3.  如果 <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> 方法傳回 `false`，則建立新的 <xref:System.Runtime.Serialization.XsdDataContractImporter> 並將其 <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> 屬性設為 <xref:System.Runtime.Serialization.ImportOptions> 類別的新執行個體。 否則使用 `out` 方法的 <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> 參數傳回的匯入工具。  
  
4.  如果 <xref:System.Runtime.Serialization.XsdDataContractImporter> 未定義任何 <xref:System.Runtime.Serialization.ImportOptions>，則將屬性設為 <xref:System.Runtime.Serialization.ImportOptions> 類別的新執行個體。  
  
5.  將 <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A> 之 <xref:System.Runtime.Serialization.ImportOptions> 的 <xref:System.Runtime.Serialization.XsdDataContractImporter> 屬性設為代理的新執行個體。  
  
6.  將 <xref:System.Runtime.Serialization.XsdDataContractImporter> 加入至 <xref:System.ServiceModel.Description.MetadataExporter.State%2A> (繼承自 <xref:System.ServiceModel.Description.WsdlImporter> 類別) 的 <xref:System.ServiceModel.Description.MetadataExporter> 屬性傳回的集合。  
  
7.  使用 <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> 的 <xref:System.ServiceModel.Description.WsdlImporter> 方法匯入結構描述內的所有資料合約。 在進行最後的步驟時，程式碼會從呼叫至代理而載入的結構描述產生。  
  
     [!code-csharp[C_IDataContractSurrogate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#9)]  
  
### <a name="to-use-a-surrogate-for-metadata-export"></a>若要使用代理進行中繼資料匯出  
 根據預設，從 WCF 匯出中繼資料服務時，需要產生 WSDL 和 XSD 結構描述。 代理必須加入至負責產生資料合約型別 <xref:System.Runtime.Serialization.XsdDataContractExporter> 的 XSD 結構描述元件中。 若要執行這項操作，可使用實作 <xref:System.ServiceModel.Description.IWsdlExportExtension> 的行為修改 <xref:System.ServiceModel.Description.WsdlExporter>，或是直接修改用來匯出中繼資料的 <xref:System.ServiceModel.Description.WsdlExporter>。  
  
##### <a name="to-use-a-surrogate-for-metadata-export"></a>若要使用代理進行中繼資料匯出  
  
1.  建立新的 <xref:System.ServiceModel.Description.WsdlExporter>，或是使用傳遞至 `wsdlExporter` 方法的 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> 參數。  
  
2.  使用 <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> 函式檢查是否已定義 <xref:System.Runtime.Serialization.XsdDataContractExporter>。  
  
3.  如果 <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> 傳回 `false`，則從 <xref:System.Runtime.Serialization.XsdDataContractExporter> 建立含有所產生 XML 結構描述的新 <xref:System.ServiceModel.Description.WsdlExporter>，並且將它加入至 <xref:System.ServiceModel.Description.MetadataExporter.State%2A> 的 <xref:System.ServiceModel.Description.WsdlExporter> 屬性傳回的集合。 否則使用 `out` 方法的 <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> 參數傳回的匯出工具。  
  
4.  如果 <xref:System.Runtime.Serialization.XsdDataContractExporter> 未定義任何 <xref:System.Runtime.Serialization.ExportOptions>，則將 <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> 屬性設為 <xref:System.Runtime.Serialization.ExportOptions> 類別的新執行個體。  
  
5.  將 <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A> 之 <xref:System.Runtime.Serialization.ExportOptions> 的 <xref:System.Runtime.Serialization.XsdDataContractExporter> 屬性設為代理的新執行個體。 後續匯出中繼資料的步驟不需要任何改變。  
  
     [!code-csharp[C_IDataContractSurrogate#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#10)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.IDataContractSurrogate>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.Runtime.Serialization.ImportOptions>  
 <xref:System.Runtime.Serialization.ExportOptions>  
 [使用資料合約](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
