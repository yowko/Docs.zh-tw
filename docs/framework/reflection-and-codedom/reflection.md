---
title: ".NET Framework 中的反映"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], reflection
- EventInfo class, reflection
- common language runtime, reflection
- FieldInfo class, reflection
- ParameterInfo class, reflection
- ConstructorInfo class, reflection
- Assembly class, reflection
- value types, reflection
- reflection, about reflection
- modules, reflection
- runtime, reflection
- Module class, reflection
- MethodInfo class, reflection
- PropertyInfo class, reflection
- type browsers
- reflection
- discovering type information at run time
- type system, reflection
ms.assetid: d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b131b8b66315ffbb769eab059142f729cfaf2a2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="reflection-in-the-net-framework"></a>.NET Framework 中的反映
<xref:System.Reflection> 命名空間中的類別，連同 <xref:System.Type?displayProperty=nameWithType>，可讓您取得已載入[組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)和其中所定義類型的資訊，例如[類別](http://msdn.microsoft.com/library/ad7d3561-271e-4546-82fc-e00b059f27a9)、[介面](http://msdn.microsoft.com/library/fd9d5975-5363-4bc9-b883-609f887895e5)和[實值型別](http://msdn.microsoft.com/library/c9c567f8-8ab1-4d88-834d-00f7d92418de)。 您也可以使用反映在執行階段建立類型執行個體，並叫用和存取它們。 如需反映特定層面的主題，請參閱此概觀結尾的[相關主題](#related_topics)。  
  
 [Common Language Runtime](../../../docs/standard/clr.md) 載入器會管理[應用程式定義域](../../../docs/framework/app-domains/application-domains.md)，這會在有相同應用程式範圍的物件周圍構成定義的界限。 這個管理包含載入每個組件至適當的應用程式定義域和控制每個組件內類型階層的記憶體配置。  
  
 [組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)包含模組、模組包含類型，而類型包含成員。 反映提供封裝組件、模組和類型的物件。 您可以使用反映來動態建立類型的執行個體、繫結類型至現有的物件，或從現有的物件取得類型。 然後，您可以叫用類型的方法或存取其欄位和屬性。 反映的一般用法包含下列幾項：  
  
-   使用 <xref:System.Reflection.Assembly> 來定義和載入組件，載入列在組件資訊清單中的模組，然後從這個組件中尋找類型並建立它的執行個體。  
  
-   使用 <xref:System.Reflection.Module> 來探索資訊，例如包含模組的組件以及模組中的類別。 您也可以取得所有全域方法，或在模組上所定義的其他特定非全域方法。  
  
-   使用 <xref:System.Reflection.ConstructorInfo> 來探索資訊，例如名稱、參數、存取修飾詞 (例如 `public` 或 `private`)，以及建構函式的實作詳細資料 (例如 `abstract` 或 `virtual`)。 使用 <xref:System.Type> 的 <xref:System.Type.GetConstructors%2A> 或 <xref:System.Type.GetConstructor%2A> 方法來叫用特定的建構函式。  
  
-   使用 <xref:System.Reflection.MethodInfo> 來探索資訊，例如名稱、傳回類型、參數、存取修飾詞 (例如 `public` 或 `private`)，以及方法的實作詳細資料 (例如 `abstract` 或 `virtual`)。 使用 <xref:System.Type> 的 <xref:System.Type.GetMethods%2A> 或 <xref:System.Type.GetMethod%2A> 方法來叫用特定的方法。  
  
-   使用 <xref:System.Reflection.FieldInfo> 來探索資訊，例如名稱、存取修飾詞 (例如 `public` 或 `private`)，以及欄位的實作詳細資料 (例如 `static`)，並取得或設定欄位值。  
  
-   使用 <xref:System.Reflection.EventInfo> 來探索資訊，例如名稱、事件處理常式資料類型、自訂屬性、宣告類型，以及事件的反映類型，並加入或移除事件處理常式。  
  
-   使用 <xref:System.Reflection.PropertyInfo> 來探索資訊，例如名稱、資料類型、宣告類型、反映類型和唯讀或可寫入的屬性狀態，並且取得或設定屬性值。  
  
-   使用 <xref:System.Reflection.ParameterInfo> 來探索資訊，例如參數的名稱、資料類型、參數是否為輸入或輸出參數以及方法簽章中的參數位置。  
  
-   當您在應用程式定義域的僅限反映之內容中工作時，請使用 <xref:System.Reflection.CustomAttributeData> 來探索自訂屬性的相關資訊。 <xref:System.Reflection.CustomAttributeData> 可讓您檢查屬性而不需建立它們的執行個體。  
  
 <xref:System.Reflection.Emit> 命名空間的類別提供一種特殊形式的反映，可讓您在執行階段建置類型。  
  
 反映也可以用來建立稱為類型瀏覽器的應用程式，可讓使用者選取類型，然後檢視這些類型的相關資訊。  
  
 反映還有其他用途。 JScript 之類的語言編譯器會使用反映來建構符號表。 <xref:System.Runtime.Serialization> 命名空間中的類別會使用反映來存取資料，並決定要保存哪個欄位。 <xref:System.Runtime.Remoting> 命名空間中的類別在序列化時會間接使用反映。  
  
## <a name="runtime-types-in-reflection"></a>反映中的執行階段類型  
 反映會提供類別，例如 <xref:System.Type> 和 <xref:System.Reflection.MethodInfo>，表示類型、成員、參數和其他程式碼實體。 不過，當您使用反映時不直接搭配類別使用，則其中大部分都會是抽象的 (在 Visual Basic 中為 `MustInherit`)。 您可改用 Common Language Runtime (CLR) 所提供的類型。  
  
 例如，當您使用 C# `typeof` 運算子 (在 Visual Basic 中為 `GetType`) 來取得 <xref:System.Type> 物件時，該物件確實為 `RuntimeType`。 `RuntimeType` 衍生自 <xref:System.Type>，並提供所有抽象方法的實作。  
  
 這些執行階段類別是 `internal` (在 Visual Basic 中為 `Friend`)。 它們不會分別從其基底類別記錄，因為它們的行為由基底類別的文件所描述。  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[檢視類型資訊](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)|描述 <xref:System.Type> 類別，並提供程式碼範例說明如何搭配幾個反映類別來使用 <xref:System.Type>，以取得建構函式、方法、欄位、屬性和事件的相關資訊。|  
|[反映和泛用類型](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)|說明反映如何處理泛型類型和泛型方法的型別參數和型別引數。|  
|[反映的安全性考量](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)|描述判斷可使用哪種程度的反映之規則，以探索類型資訊和存取類型。|  
|[動態載入和使用類型](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md)|描述支援晚期繫結的反映自訂繫結介面。|  
|[操作說明：將組件載入僅限反映的內容](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|描述僅限反映的載入內容。 示範如何載入組件、如何測試內容，以及如何檢查套用至僅限反映的內容中組件的屬性。|  
|[存取自訂屬性](../../../docs/framework/reflection-and-codedom/accessing-custom-attributes.md)|示範如何使用反映來查詢屬性是否存在和屬性的值。|  
|[指定完整的類型名稱](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)|描述完整的類型名稱之格式，根據巴克斯格式 (BNF)，以及指定特殊字元、組件名稱、指標、參考和陣列所需的語法來描述。|  
|[如何：使用反映連結委派](../../../docs/framework/reflection-and-codedom/how-to-hook-up-a-delegate-using-reflection.md)|說明如何建立方法的委派，以及連結委派到事件。 說明如何在執行階段使用 <xref:System.Reflection.Emit.DynamicMethod> 建立事件處理方法。|  
|[發出動態方法和組件](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|說明如何產生動態組件和動態方法。|  
  
## <a name="reference"></a>參考資料  
 <xref:System.Type?displayProperty=nameWithType>  
  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
