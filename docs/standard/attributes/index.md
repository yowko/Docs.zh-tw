---
title: 使用屬性擴充中繼資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- metadata, extending
- attributes [.NET Framework], metadata
- elements [.NET Framework], attributes
- common language runtime, attributes
- annotating programming elements
- keyword-like descriptive declarations
- runtime, attributes
- extending metadata
ms.assetid: 30386922-1e00-4602-9ebf-526b271a8b87
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a31082604048e71ebc7581b36857a8bfbd333c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969789"
---
# <a name="extending-metadata-using-attributes"></a>使用屬性擴充中繼資料
Common Language Runtime 可讓您加入稱為屬性 (Attribute) 之類似關鍵字的描述性宣告，以標註類型、欄位、方法和屬性 (Property) 等程式設計項目。 當您編譯執行階段的程式碼時，它會轉換成 Microsoft 中繼語言 (MSIL)，並與編譯器所產生的中繼資料一起放在可攜式執行檔 (PE) 中。 屬性可讓您將額外的描述性資訊放入中繼資料，其可使用執行階段反映服務來擷取。 編譯器會在您宣告衍生自 <xref:System.Attribute?displayProperty=nameWithType> 的特殊類別執行個體時建立屬性。  
  
 .NET Framework 會針對各種原因使用屬性來解決一些問題。 屬性描述如何序列化資料、指定用來強制執行安全性的特性，以及限制 Just-in-Time (JIT) 編譯器的最佳化程度，讓程式碼保持易於偵錯。 屬性也可記錄檔案名稱或程式碼作者，或者在表單開發期間控制控制項和成員的可見性。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|說明|  
|-----------|-----------------|  
|[套用屬性](../../../docs/standard/attributes/applying-attributes.md)|描述如何將屬性套用至您程式碼的項目。|  
|[撰寫自訂屬性](../../../docs/standard/attributes/writing-custom-attributes.md)|描述如何設計自訂屬性類別。|  
|[擷取儲存於屬性中的資訊](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)|描述如何針對載入執行內容中的程式碼擷取自訂屬性。|  
|[中繼資料和自我描述元件](../../../docs/standard/metadata-and-self-describing-components.md)|提供中繼資料的概觀，並描述如何在 .NET Framework 可攜式執行檔 (PE) 中實作。|  
|[如何：將組件載入到僅限反映的內容將組件載入到僅限反映的內容](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|說明如何擷取僅限反映的內容中的自訂屬性資訊。|  
  
## <a name="reference"></a>參考資料  
 <xref:System.Attribute?displayProperty=nameWithType>
