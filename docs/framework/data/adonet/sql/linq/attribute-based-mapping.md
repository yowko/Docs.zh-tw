---
title: 屬性架構對應
ms.date: 03/30/2017
ms.assetid: 6dd89999-f415-4d61-b8c8-237d23d7924e
ms.openlocfilehash: 1e11a2efc3d1afa56a27d6e2c60149a509511080
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248068"
---
# <a name="attribute-based-mapping"></a>屬性架構對應
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]藉由套用屬性或使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]外部對應檔，將 SQL Server 資料庫對應至物件模型。 本主題概述以屬性 (Attribute) 為基礎的方法。  
  
 以最基本形式存在的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將資料庫對應至 <xref:System.Data.Linq.DataContext>、將資料表對應至類別，並且將資料行和關聯性 (Relationship) 對應至這些類別中的屬性 (Property)。 您也可以使用屬性 (Attribute) 來對應物件模型中的繼承階層架構 (Inheritance Hierarchy)。 如需詳細資訊，請參閱[如何：在 Visual Basic 或C# ](how-to-generate-the-object-model-in-visual-basic-or-csharp.md)中產生物件模型。  
  
 使用 Visual Studio 的開發人員通常會使用物件關聯式設計工具來執行以屬性為基礎的對應。 您也可以使用 SQLMetal 命令列工具，或者自行撰寫屬性的程式碼。 如需詳細資訊，請參閱[如何：在 Visual Basic 或C# ](how-to-generate-the-object-model-in-visual-basic-or-csharp.md)中產生物件模型。  
  
> [!NOTE]
> 您也可以使用外部 XML 檔進行對應。 如需詳細資訊，請參閱[外部對應](external-mapping.md)。  
  
 下列各節會詳細說明以屬性 (Attribute) 為基礎的對應。 如需詳細資訊，請參閱 <xref:System.Data.Linq.Mapping>。  
  
## <a name="databaseattribute-attribute"></a>DatabaseAttribute 屬性  
 當連接未提供資料庫名稱時，請使用這個屬性 (Attribute) 指定資料庫的預設名稱。 這個屬性 (Attribute) 為選擇性屬性，但如果您加以使用，就必須套用 <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> 屬性 (Property)，如下表中的說明。  
  
|屬性|類型|預設|描述|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>|String|請參閱<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>|搭配其 <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> 屬性 (Property) 使用，可以指定資料庫的名稱。|  
  
 如需詳細資訊，請參閱 <xref:System.Data.Linq.Mapping.DatabaseAttribute>。  
  
## <a name="tableattribute-attribute"></a>TableAttribute 屬性  
 使用這個屬性可以指定某個類別，做為與資料庫資料表或檢視相關聯的實體類別。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將具有這個屬性的類別視為持續性類別。 下表說明 <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> 屬性 (Property)。  
  
|屬性|類型|預設|說明|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.TableAttribute.Name%2A>|String|與類別名稱相同的字串|指定某個類別，做為與資料庫資料表相關聯的實體類別。|  
  
 如需詳細資訊，請參閱 <xref:System.Data.Linq.Mapping.TableAttribute>。  
  
## <a name="columnattribute-attribute"></a>ColumnAttribute 屬性  
 使用這個屬性 (Attribute) 可以指定實體類別的成員，以代表資料庫資料表中的資料行。 您可以將這個屬性 (Attribute) 套用至任何欄位或屬性 (Property)。  
  
 當 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 將變更儲存至資料庫時，只會擷取和保存經您識別為資料行的成員。 不具此屬性 (Attribute) 的成員會被認為是非持續性的成員，而不會送出以進行插入或更新。  
  
 下表說明這個屬性 (Attribute) 的屬性 (Property)。  
  
|屬性|類型|預設|描述|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>|AutoSync|永不|指示 Common Language Runtime (CLR) 在插入或更新作業之後擷取值。<br /><br /> 選項:Always、Never、OnUpdate、OnInsert。|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>|Boolean|`true`|表示資料行可以包含 Null 值。|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>|String|推斷的資料庫資料行型別|使用資料庫型別和修飾詞 (Modifier) 來指定資料庫資料行的型別。|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>|String|Empty|定義資料庫中的計算資料行。|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>|Boolean|`false`|表示資料行含有資料庫自動產生的值。|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A>|Boolean|`false`|表示資料行含有 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 繼承階層架構 (Inheritance Hierarchy) 所需的鑑別子值。|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>|Boolean|`false`|表示這個類別成員是資料表的主索引鍵 (可能是唯一一個也可能是多個主索引鍵之一)。|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>|Boolean|`false`|以資料庫時間戳記或版本號碼識別成員的資料行型別。|  
|<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>|UpdateCheck|`Always`，除非成員的 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 為 `true`|指定 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 如何進行開放式並行存取衝突的偵測。|  
  
 如需詳細資訊，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute>。  
  
> [!NOTE]
> AssociationAttribute 和 ColumnAttribute Storage 屬性值會區分大小寫。 例如，請確定用於 AssociationAttribute.Storage 屬性 (Property) 之屬性 (Attribute) 中的值與用於程式碼中其他位置之對應屬性 (Property) 名稱的大小寫相符。 這適用于所有的 .NET 程式設計語言，即使通常不會區分大小寫，包括 Visual Basic。 如需 Storage 屬性的詳細資訊，請參閱 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>。  
  
## <a name="associationattribute-attribute"></a>AssociationAttribute 屬性  
 使用這個屬性 (Attribute) 可以指定屬性 (Property)，以代表資料庫中的關聯，例如外部索引鍵對主索引鍵的關聯性。 如需關聯性的詳細資訊[，請參閱如何：對應資料庫關聯性](how-to-map-database-relationships.md)。  
  
 下表說明這個屬性 (Attribute) 的屬性 (Property)。  
  
|屬性|類型|預設|描述|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.DeleteOnNull%2A>|Boolean|`false`|如果位於外部索引鍵成員都不可為 null 的關聯上，則會在關聯設為 null 時刪除物件。|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.DeleteRule%2A>|String|無|將刪除行為加入至關聯。|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.IsForeignKey%2A>|Boolean|`false`|若為 true，則指定這個成員做為代表資料庫關聯性之關聯中的外部索引鍵。|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.IsUnique%2A>|Boolean|`false`|若為 true，則表示外部索引鍵有唯一性條件約束。|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A>|String|相關類別的 ID|指定目標實體類別的一個或多個成員，做為關聯另一端的索引值。|  
|<xref:System.Data.Linq.Mapping.AssociationAttribute.ThisKey%2A>|String|包含類別的 ID|指定這個實體類別的成員代表關聯這一端的索引值。|  
  
 如需詳細資訊，請參閱 <xref:System.Data.Linq.Mapping.AssociationAttribute>。  
  
> [!NOTE]
> AssociationAttribute 和 ColumnAttribute Storage 屬性值會區分大小寫。 例如，請確定用於 AssociationAttribute.Storage 屬性 (Property) 之屬性 (Attribute) 中的值與用於程式碼中其他位置之對應屬性 (Property) 名稱的大小寫相符。 這適用于所有的 .NET 程式設計語言，即使通常不會區分大小寫，包括 Visual Basic。 如需 Storage 屬性的詳細資訊，請參閱 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>。  
  
## <a name="inheritancemappingattribute-attribute"></a>InheritanceMappingAttribute 屬性  
 使用這個屬性可以對應繼承階層架構。  
  
 下表說明這個屬性 (Attribute) 的屬性 (Property)。  
  
|屬性|類型|預設|說明|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>|String|無。 必須提供值。|指定鑑別子的程式碼值。|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>|Boolean|`false`|若為 true，則在存放區中沒有鑑別子值符合所指定的任何一個值時，具現化這個型別的物件。|  
|<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>|類型|無。 必須提供值。|指定階層架構中這個類別的型別。|  
  
 如需詳細資訊，請參閱 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>。  
  
## <a name="functionattribute-attribute"></a>FunctionAttribute 屬性  
 使用這個屬性可以指定方法，以代表資料庫中的預存程序或使用者定義的函式。  
  
 下表說明這個屬性 (Attribute) 的屬性 (Property)。  
  
|屬性|類型|預設|描述|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A>|Boolean|`false`|若為 false，則表示對應至預存程序。 若為 true，則表示對應至使用者定義函式。|  
|<xref:System.Data.Linq.Mapping.FunctionAttribute.Name%2A>|String|與資料庫中的名稱相同的字串|指定預存程序或使用者定義函式的名稱。|  
  
 如需詳細資訊，請參閱 <xref:System.Data.Linq.Mapping.FunctionAttribute>。  
  
## <a name="parameterattribute-attribute"></a>ParameterAttribute 屬性  
 使用這個屬性可以對應預存程序方法的輸入參數。  
  
 下表說明這個屬性 (Attribute) 的屬性 (Property)。  
  
|屬性|類型|預設|描述|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ParameterAttribute.DbType%2A>|String|無|指定資料庫型別。|  
|<xref:System.Data.Linq.Mapping.ParameterAttribute.Name%2A>|String|與資料庫中的參數名稱相同的字串|指定參數的名稱。‏|  
  
 如需詳細資訊，請參閱 <xref:System.Data.Linq.Mapping.ParameterAttribute>。  
  
## <a name="resulttypeattribute-attribute"></a>ResultTypeAttribute 屬性  
 使用這個屬性可以指定結果型別。  
  
 下表說明這個屬性 (Attribute) 的屬性 (Property)。  
  
|屬性|類型|預設|說明|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.ResultTypeAttribute.Type%2A>|類型|(無)|用在對應至會傳回 <xref:System.Data.Linq.IMultipleResults> 之預存程序的方法中。 宣告預存程序的有效或應有的型別對應。|  
  
 如需詳細資訊，請參閱 <xref:System.Data.Linq.Mapping.ResultTypeAttribute>。  
  
## <a name="dataattribute-attribute"></a>DataAttribute 屬性  
 使用這個屬性可以指定名稱和私用儲存欄位。  
  
 下表說明這個屬性 (Attribute) 的屬性 (Property)。  
  
|屬性|類型|預設|描述|  
|--------------|----------|-------------|-----------------|  
|<xref:System.Data.Linq.Mapping.DataAttribute.Name%2A>|String|與資料庫中的名稱相同|指定資料表、資料行等的名稱。|  
|<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>|String|公用存取子|指定基礎儲存欄位的名稱。|  
  
 如需詳細資訊，請參閱 <xref:System.Data.Linq.Mapping.DataAttribute>。  
  
## <a name="see-also"></a>另請參閱

- [參考資料](reference.md)
