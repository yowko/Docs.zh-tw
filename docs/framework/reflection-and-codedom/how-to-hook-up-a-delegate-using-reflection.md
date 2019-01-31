---
title: HOW TO：使用反映連結委派
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe90542d1ba106dd52e8995afab298b4b9f69899
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54644387"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a>HOW TO：使用反映連結委派
當您使用反映來載入和執行組件時，無法使用 C# `+=` 運算子或 Visual Basic [AddHandler 陳述式](~/docs/visual-basic/language-reference/statements/addhandler-statement.md)這類語言功能來連結事件。 下列程序示範如何透過反映取得所有必要類型以將現有方法連結至事件，以及如何使用反映發出建立動態方法並將它連結至事件。  
  
> [!NOTE]
>  如需連結事件處理委派的另一種方式，請參閱 <xref:System.Reflection.EventInfo> 類別之 <xref:System.Reflection.EventInfo.AddEventHandler%2A> 方法的程式碼範例。  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a>使用反映連結委派  
  
1.  載入包含引發事件之類型的組件。 通常會使用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法載入組件。 為了簡化此範例，會使用目前組件中的衍生形式，因此使用 <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> 方法來載入目前組件。  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2.  取得代表類型的 <xref:System.Type> 物件，並建立類型的執行個體。 因為表單具有預設建構函式，所以在下列程式碼中使用 <xref:System.Activator.CreateInstance%28System.Type%29> 方法。 如果您所建立的類型沒有預設建構函式，則 <xref:System.Activator.CreateInstance%2A> 方法有數個其他多載可以使用。 新的執行個體會儲存為 <xref:System.Object> 類型，以維護不知道組件的故事 (反映可讓您取得組件中的類型，而不需要事先知道其名稱)。  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3.  取得代表事件的 <xref:System.Reflection.EventInfo> 物件，並使用 <xref:System.Reflection.EventInfo.EventHandlerType%2A> 屬性來取得用來處理事件之委派的類型。 在下列程式碼中，會取得 <xref:System.Windows.Forms.Control.Click> 事件的 <xref:System.Reflection.EventInfo>。  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4.  取得代表處理事件之方法的 <xref:System.Reflection.MethodInfo> 物件。 本主題後段的＜範例＞一節中的完整程式碼，包含了與 <xref:System.EventHandler> 委派的簽章相符的方法，此委派會處理 <xref:System.Windows.Forms.Control.Click> 事件，但是您也可以在執行階段產生動態方法。 如需詳細資訊，請參閱伴隨的程序中關於在執行階段使用動態方法產生事件處理常式的資訊。  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5.  使用 <xref:System.Delegate.CreateDelegate%2A> 方法，建立委派的執行個體。 此方法是 static (在 Visual Basic 中為 `Shared`)，因此必須提供委派類型。 建議使用接受 <xref:System.Reflection.MethodInfo> 之 <xref:System.Delegate.CreateDelegate%2A> 的多載。  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6.  取得 `add` 存取子方法，並叫用它來連結事件。 所有事件都有高階語言語法所隱藏的 `add` 存取子和 `remove` 存取子。 例如，C# 使用 `+=` 運算子來連結事件，Visual Basic 則使用 [AddHandler 陳述式](~/docs/visual-basic/language-reference/statements/addhandler-statement.md)。 下列程式碼會取得 <xref:System.Windows.Forms.Control.Click> 事件的 `add` 存取子，以及透過晚期繫結叫用它，並傳入委派執行個體。 引數必須傳遞為陣列。  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7.  測試事件。 下列程式碼顯示程式碼範例中所定義的表單。 按一下表單，會叫用事件處理常式。  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a>使用動態方法以在執行階段產生事件處理常式  
  
1.  使用輕量型動態方法和反映發出，可以在執行階段產生事件處理常式方法。 若要建構事件處理常式，您需要委派的傳回型別和參數類型。 這些可以透過檢查委派的 `Invoke` 方法取得。 下列程式碼使用 `GetDelegateReturnType` 和 `GetDelegateParameterTypes` 方法來取得這項資訊。 這些方法的程式碼位於本主題稍後的＜範例＞一節中。  
  
     不需要命名 <xref:System.Reflection.Emit.DynamicMethod>，因此可以使用空字串。 在下列程式碼中，最後一個引數會建立動態方法與目前類型的關聯，並提供 `Example` 類別之所有公用和私用成員的委派存取權。  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2.  產生方法主體。 這個方法會載入字串、呼叫接受字串之 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> 方法的多載、從堆疊取出傳回值 (因為處理常式沒有傳回型別) 並傳回。 若要深入了解如何發出動態方法，請參閱[如何：定義和執行動態方法](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)。  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3.  呼叫 <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> 方法，以完成動態方法。 使用 `add` 存取子，以將委派新增至事件的叫用清單。  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4.  測試事件。 下列程式碼會載入程式碼範例中所定義的表單。 按一下表單，會叫用預先定義的事件處理常式和發出的事件處理常式。  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何使用反映以將現有方法連結至事件，同時示範如何使用 <xref:System.Reflection.Emit.DynamicMethod> 類別以在執行階段發出方法，並將它連結至事件。  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   此程式碼包含編譯所需的 C# `using` 陳述式 (Visual Basic 為 `Imports`)。  
  
-   不需要任何其他組件參考，即可從命令列進行編譯。 在 Visual Studio 中，您必須新增 System.Windows.Forms.dll 的參考，因為這個範例是主控台應用程式。  
  
-   在命令列使用 csc.exe、vbc.exe 或 cl.exe 編譯程式碼。 若要編譯 Visual Studio 中的程式碼，請將它放在主控台應用程式專案範本。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [如何：定義和執行動態方法](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)
- [反映](../../../docs/framework/reflection-and-codedom/reflection.md)
