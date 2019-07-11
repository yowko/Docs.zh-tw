---
title: Serialization2
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a15ae411-8dc2-4ca3-84d2-01c9d5f1972a
ms.openlocfilehash: 1ff6f8b58e01c86ae1c1e2e1533b1997ba2eb6b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742896"
---
# <a name="serialization"></a>序列化
本主題描述[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]序列化功能。 後續段落會提供有關如何在設計階段的程式碼產生期間加入序列化以及 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 類別 (Class) 的執行階段序列化行為。  
  
 您可以透過下列其中一種方法，在設計階段加入序列化程式碼：  
  
- 在 物件關聯式設計工具中，變更**序列化模式**屬性設**單向**。  
  
- 在 SQLMetal 命令列中，新增 **/serialization**選項。 如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)。  
  
## <a name="overview"></a>總覽  
 產生的程式碼[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]預設會提供延後的載入功能。 在視需要透明載入資料的中介層中，延後載入非常方便。 但是，由於不論是否需要延後載入，序列化程式都會觸發延後載入，所以序列化會有問題。 事實上，序列化物件後，在所有傳出延後載入的參考之下的遞移封閉 (Transitive Closure) 也已序列化。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]序列化功能會處理這個問題，主要是透過兩種機制：  
  
- 用於關閉延後載入的 <xref:System.Data.Linq.DataContext> 模式 (<xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A>)。 如需詳細資訊，請參閱 <xref:System.Data.Linq.DataContext>。  
  
- 程式碼產生參數，用在產生的實體上產生 <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> 和 <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> 屬性 (Attribute)。 這個方面 (包含序列化之下延後載入類別的行為) 為本主題的主旨。  
  
### <a name="definitions"></a>定義  
  
- *DataContract 序列化程式*:預設為.NET Framework 3.0 或更新版本的 Windows Communication Framework (WCF) 元件所使用的序列化程式。  
  
- *單向序列化*:包含僅單向關聯屬性 （以避免循環） 之類別的序列化的版本。 依照慣例，主索引鍵-外部索引鍵關聯性之父端上的屬性 (Poperty) 會標記為即將序列化。 雙向關聯中的另一端則不會序列化。  
  
     單向序列化是 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 唯一支援的序列化類型。  
  
## <a name="code-example"></a>程式碼範例  
 下列程式碼會使用 Northwind 範例資料庫中的傳統 `Customer` 和 `Order` 類別，並且顯示如何使用序列化屬性 (Attribute) 裝飾這些類別。  
  
 [!code-csharp[DLinqSerialization#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#1)]
 [!code-vb[DLinqSerialization#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#1)]  
  
 [!code-csharp[DLinqSerialization#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#2)]
 [!code-vb[DLinqSerialization#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#2)]  
  
 [!code-csharp[DLinqSerialization#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#3)]
 [!code-vb[DLinqSerialization#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#3)]  
  
 至於下列範例中的 `Order` 類別，只有對應至 `Customer` 類別的反向關聯屬性 (Property) 會簡短顯示。 該類別沒有 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 (Attribute) 可避免循環。  
  
 [!code-csharp[DLinqSerialization#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#4)]
 [!code-vb[DLinqSerialization#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#4)]  
  
 [!code-csharp[DLinqSerialization#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#5)]
 [!code-vb[DLinqSerialization#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#5)]  
  
### <a name="how-to-serialize-the-entities"></a>如何將實體序列化  
 您可以在上一節顯示的程式碼中將實體序列化，如下所示：  
  
 [!code-csharp[DLinqSerialization#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/Program.cs#6)]
 [!code-vb[DLinqSerialization#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/Module1.vb#6)]  
  
### <a name="self-recursive-relationships"></a>自我遞迴關聯性  
 自我遞迴關聯性會依循相同的模式。 對應至外部索引鍵的關聯屬性 (Property) 沒有 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 (Attribute)，然而父屬性 (Property) 卻有該屬性 (Attribute)。  
  
 請考慮下列具有兩個自我遞迴關聯性的類別：Employee.manager/reports 和 employee.mentor/mentees。  
  
 [!code-csharp[DLinqSerialization#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#7)]
 [!code-vb[DLinqSerialization#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#7)]  
  
## <a name="see-also"></a>另請參閱

- [背景資訊](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [SqlMetal.exe (程式碼產生工具)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [如何：讓實體可序列化](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)
