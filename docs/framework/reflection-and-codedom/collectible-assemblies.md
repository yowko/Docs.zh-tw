---
title: "動態類型產生可回收組件"
description: 
ms.date: 08/29/2017
ms.prod: .net
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reflection, dynamic assembly
- assemblies, collectible
- collectible assemblies, retrieving
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2c9a613f4cc13c3e4189a59ace2e05d01d1bcb4f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="collectible-assemblies-for-dynamic-type-generation"></a>動態類型產生可回收組件

*可回收組件*是動態組件，而不卸載它們建立所在的應用程式定義域可以卸載。 可回收組件和它所包含的型別所使用的所有 managed 和 unmanaged 記憶體回收。 組件名稱等資訊是從內部資料表中移除。

若要啟用卸載，請使用<xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndCollect?displayProperty=nameWithType>旗標，當您建立動態組件。 組件是暫時性 （也就是它不能儲存） 而且受限於中所述限制[可回收組件的限制](#restrictions-on-collectible-assemblies)> 一節。 Common language runtime (CLR) 會自動卸載可回收組件，當您發行組件相關聯的所有物件。 在其他方面，可回收組件會建立和使用方式與其他動態組件相同。

## <a name="lifetime-of-collectible-assemblies"></a>可回收組件的存留期

可回收組件的存留期會控制所包含的類型以及從這些型別所建立的物件參考存在。 Common language runtime 不會卸載組件，只要有一個或多個項目存在 (`T`組件中定義的所有類型): 

- `T` 的執行個體。

- 陣列的執行個體`T`。
 
- 具有泛型類型的執行個體`T`做為其中一個型別引數。 這包括的泛型集合`T`，即使該集合是空的。

- 執行個體<xref:System.Type>或<xref:System.Reflection.Emit.TypeBuilder>表示`T`。 

   > [!IMPORTANT]
   > 您必須釋放所有物件，代表組件的部分。 <xref:System.Reflection.Emit.ModuleBuilder>定義`T`會保留參考<xref:System.Reflection.Emit.TypeBuilder>，而<xref:System.Reflection.Emit.AssemblyBuilder>物件會保留參考<xref:System.Reflection.Emit.ModuleBuilder>，因此必須釋放這些物件的參考。 即使有<xref:System.Reflection.Emit.LocalBuilder>或<xref:System.Reflection.Emit.ILGenerator>之建構中使用`T`可避免卸載。

- 靜態參考`T`其他動態定義的型別來`T1`這仍可執行程式碼。 例如，`T1`可能會衍生自`T`，或`T`可能是在方法中參數的型別`T1`。
 
- A **ByRef**至靜態欄位所屬`T`。

- A <xref:System.RuntimeTypeHandle>， <xref:System.RuntimeFieldHandle>，或<xref:System.RuntimeMethodHandle>參考`T`或元件的`T`。

- 執行任何的個體無法間接使用的反映物件或直接存取<xref:System.Type>物件，代表`T`。 例如，<xref:System.Type>物件`T`可以從其項目類型是陣列型別取得`T`，或從具有泛型型別`T`作為類型引數。 

- 方法`M`任何執行緒的呼叫堆疊上其中`M`是一種方法的`T`或組件中定義的模組層級方法。

- 定義組件的模組中的靜態方法的委派。

如果只有一個項目從這個清單有只有一個型別或組件中的一個方法，執行階段無法卸載組件。

> [!NOTE]
> 執行階段不會實際卸載組件清單中的所有項目執行完成項之前。

基於追蹤存留期的詳細資訊，建構的泛型類型例如`List<int>`（C# 中） 或`List(Of Integer)`（在 Visual Basic)，是建立，而且用於產生可回收組件會被視為已定義組件中，包含泛型類型定義，或是在組件包含的其中一個型別引數的定義。 使用的確切組件是實作詳細資料和可能有所變更。
 
## <a name="restrictions-on-collectible-assemblies"></a>可回收組件的限制

下列限制適用於可回收組件： 

- **靜態參考**   
  一般的動態組件中的類型不能有靜態參考可回收組件中定義的類型。 例如，如果您定義一般型別繼承自可回收組件中的型別<xref:System.NotSupportedException>擲回例外狀況。 可回收組件中的型別可以有類型的靜態參考另一個可回收組件，但這會擴充參考的組件參考的組件的存留期的存留期。

- **COM interop**   
   COM 介面都不可以定義內可回收組件，並為可回收組件中類型的任何執行個體都可以轉換為 COM 物件。 可回收組件中的類型不能做為 COM 可呼叫包裝函式 (CCW) 或執行階段可呼叫包裝函式 (RCW)。 不過，可回收組件中的型別可以使用實作 COM 介面的物件。

- **平台叫用**   
   具有方法<xref:System.Runtime.InteropServices.DllImportAttribute>可回收組件中宣告時，不會編譯屬性。 <xref:System.Reflection.Emit.OpCodes.Calli?displayProperty=nameWithType>指令不能用於在可回收組件，類型的實作，這類類型無法封送處理至 unmanaged 程式碼。 不過，您可以呼叫原生程式碼使用宣告非可回收組件中的進入點。
 
- **封送處理**   
   無法封送處理 （特別是在委派） 中可回收組件中定義的物件。 這是所有的暫時性發出型別上的限制。

- **載入的組件**   
   反映發出時，才支援載入可回收組件的唯一機制。 載入使用其他任何形式的組件載入的組件無法卸載。
 
- **內容繫結物件**    
   不支援 context 靜態變數。 可回收組件中的類型無法擴充<xref:System.ContextBoundObject>。 不過，可回收組件中的程式碼可以其他地方使用內容繫結所定義的物件。

- **執行緒靜態資料**       
   不支援執行緒靜態變數。

## <a name="see-also"></a>請參閱

[發出動態方法和組件](emitting-dynamic-methods-and-assemblies.md)
