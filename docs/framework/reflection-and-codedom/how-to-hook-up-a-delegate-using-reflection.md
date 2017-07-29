---
title: "如何：使用反映連結委派 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "委派 [.NET Framework], 使用反映加入事件處理常式"
  - "事件 [.NET Framework], 使用反映加入事件處理常式"
  - "反映, 加入事件處理常式委派"
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：使用反映連結委派
當您使用反映 \(Reflection\) 來載入及執行組件時，將無法使用類似 C\# `+=` 運算子或 Visual Basic [AddHandler 陳述式](../../../ocs/visual-basic/language-reference/statements/addhandler-statement.md)的語言功能來連結事件。  下列程序將示範如何透過反映取得所有必要的型別，以將現有的方法連結到事件，以及如何使用反映發出建立動態方法，並將它連結到事件。  
  
> [!NOTE]
>  如需連結事件處理委派 \(Delegate\) 的另一個方法，請參閱 <xref:System.Reflection.EventInfo> 類別之 <xref:System.Reflection.EventInfo.AddEventHandler%2A> 方法的程式碼範例。  
  
### 若要使用反映來連結委派  
  
1.  載入包含可引發事件之型別的組件；  組件通常是利用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> 方法載入。  為了要維持此範例的簡單性，會使用目前組件中的衍生表單，以便使用 <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> 方法來載入目前的組件。  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2.  取得表示此型別的 <xref:System.Type> 物件，並建立此型別的執行個體。  下列程式碼中會使用 <xref:System.Activator.CreateInstance%28System.Type%29> 方法，因為表單有預設建構函式。  如果您所建立的型別沒有預設建構函式，您可以使用數個其他的 <xref:System.Activator.CreateInstance%2A> 方法多載。  新的執行個體會儲存為型別 <xref:System.Object>，以維護對組件一無所知的假定。\(反映可讓您取得組件中的型別，而不需要事先知道其名稱\)。  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3.  取得表示此事件的 <xref:System.Reflection.EventInfo> 物件，並使用 <xref:System.Reflection.EventInfo.EventHandlerType%2A> 屬性來取得用來處理此事件的委派型別。  在下列程式碼中，會取得 <xref:System.Windows.Forms.Control.Click> 事件的 <xref:System.Reflection.EventInfo>。  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4.  取得 <xref:System.Reflection.MethodInfo> 物件，其表示處理事件的方法。  此主題之後的範例章節中，完整程式碼包含了與<xref:System.EventHandler>委派簽章符合的方法，此委派可處理 <xref:System.Windows.Forms.Control.Click> 事件，但是您也可以在執行階段產生動態方法。  如需詳細資訊，請參閱隨附的程序中關於在執行階段使用動態方法來產生事件處理常式。  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5.  使用 <xref:System.Delegate.CreateDelegate%2A> 方法建立此委派的執行個體。  這個方法為靜態 \(Visual Basic 中為 `Shared`\)，所以必須提供委派型別。  建議使用可接受 <xref:System.Reflection.MethodInfo> 的 <xref:System.Delegate.CreateDelegate%2A> 多載。  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6.  取得 `add` 存取子方法，並叫用它來連結事件。  所有的事件都有 `add` 存取子和 `remove` 存取子，這兩個存取子會由高階語言的語法所隱藏。  例如，C\# 會使用 `+=` 運算子來連結事件，而 Visual Basic 則會使用 [AddHandler 陳述式](../../../ocs/visual-basic/language-reference/statements/addhandler-statement.md)。  下列程式碼會取得 <xref:System.Windows.Forms.Control.Click> 事件的 `add` 存取子，並以晚期繫結的形式來叫用它，傳入委派執行個體；  引數必須以陣列的形式傳遞。  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7.  測試事件。  下列程式碼將顯示此程式碼範例中所定義的表單；  按一下表單，即可叫用事件處理常式。  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### 若要在執行階段使用動態方法來產生事件處理常式  
  
1.  可以在執行階段產生事件處理常式方法，其方式是使用輕量型動態方法和反映發出。  若要建構事件處理常式，您需要此委派的傳回型別和參數型別；  可以藉由檢查此委派的 `Invoke` 方法來取得這些型別。  下列程式碼使用 `GetDelegateReturnType` 和 `GetDelegateParameterTypes` 方法來取得這項資訊，  而這些方法的程式碼則可以在這個主題之後的範例一節中找到。  
  
     不需要命名 <xref:System.Reflection.Emit.DynamicMethod>，所以可以使用空字串。  在下列程式碼中，最後一個引數會將動態方法與目前的型別產生關聯，將委派存取提供給 `Example` 類別的所有公用和私用成員。  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2.  產生方法主體。  這個方法會載入字串、呼叫可接受字串之 <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> 方法的多載，將傳回值從堆疊中移除 \(因為處理常式沒有傳回型別\)，然後傳回。  若要進一步了解有關發出動態方法，請參閱 [如何：定義和執行動態方法](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)。  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3.  完成動態方法，其方式是呼叫它的 <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> 方法。  使用 `add` 存取子，將此委派加入到事件的引動過程清單中。  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4.  測試事件。  下列程式碼將載入此程式碼範例中所定義的表單；  按一下表單可叫用預先定義的事件處理常式和發出的事件處理常式兩者。  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## 範例  
 下列程式碼範例將示範如何使用反映，將現有的方法與事件連結，也將示範如何使用 <xref:System.Reflection.Emit.DynamicMethod> 類別於執行階段發出方法，並將它與事件連結。  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## 編譯程式碼  
  
-   此程式碼含有進行編譯所需的 C\# `using` 陳述式 \(Visual Basic 中的 `Imports`\)。  
  
-   從命令列進行編譯並不需要額外的組件參考；  在 Visual Studio 中，您必須將參考加入到 System.Windows.Forms.dll，因為此範例為主控台應用程式。  
  
-   使用 csc.exe、vbc.exe 或 cl.exe 在命令列編譯程式碼。  若要在 Visual Studio 中編譯程式碼，請將程式碼放在主控台應用程式專案範本中。  
  
## 請參閱  
 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>   
 <xref:System.Reflection.Emit.DynamicMethod>   
 <xref:System.Activator.CreateInstance%2A>   
 <xref:System.Delegate.CreateDelegate%2A>   
 [如何：定義和執行動態方法](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)   
 [反映](../../../docs/framework/reflection-and-codedom/reflection.md)