---
title: 逐步解說：在 Visual Studio 中，從 managed 元件內嵌類型
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1f32bd840efa97b62097a2d051c25d519785b381
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973268"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a>逐步解說：在 Visual Studio 中，從 managed 元件內嵌類型

若要內嵌來自強式名稱 Managed 組件的類型資訊，您可以鬆散地結合應用程式中的類型以確保版本獨立。 也就是說，您的程式可以撰寫成使用來自任何版本之 managed 程式庫的類型，而不需要針對每個新版本重新編譯。

內嵌型別時，通常會搭配使用 COM Interop (例如從 Microsoft Office 使用 Automation 物件的應用程式)。 當您內嵌類型資訊時，可讓相同組建的程式使用不同電腦上版本各異的 Microsoft Office。 不過，您也可以將類型內嵌用於完全受控的解決方案。

在您指定可以內嵌的公用介面之後，就可以建立執行這些介面的執行時間類別。 用戶端程式可以藉由參考包含公用介面的元件，並將參考的`Embed Interop Types`屬性設定為`True`，在設計階段內嵌介面的類型資訊。 然後，用戶端程式可以載入以這些介面類別型輸入之執行時間物件的實例。 這相當於使用命令列編譯器，並使用 `/link` 編譯器選項來參考組件。 

如果您建立新版本的強式名稱執行時間元件，則不需要重新編譯用戶端程式。 用戶端程式會繼續使用任何版本的執行時間元件，並使用公用介面的內嵌類型資訊。

在本逐步解說中, 您會:

1. 建立具有公用介面的強式名稱元件，其中包含可內嵌的類型資訊。
1. 建立強式名稱的執行時間元件，以執行公用介面。
1. 建立用戶端程式，以內嵌公用介面的類型資訊，並從執行階段組件建立類別的執行個體。
1. 修改並重新建置執行階段組件。
1. 執行用戶端程式，以查看它是否使用新版本的執行時間元件，而不需要重新編譯。

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a>條件和限制

在下列情況下，您可以從元件內嵌類型資訊： 

- 組件已公開至少一個公用介面。
- 內嵌的介面會以`ComImport`具有唯一 guid 的屬性和`Guid`屬性來標注。
- 您可以使用 `ImportedFromTypeLib` 屬性或 `PrimaryInteropAssembly` 屬性及組件層級 `Guid` 屬性，來標註組件 根據預設C# ，視覺效果和 Visual Basic 專案範本包含元件`Guid`層級屬性。

因為內嵌類型的主要功能是支援 COM Interop 元件，所以當您在完全受控的方案中嵌入類型資訊時，會有下列限制：

- 僅內嵌 COM Interop 特定的屬性。 其他屬性則會被忽略。
- 如果類型使用泛型參數，且泛型參數的類型是內嵌類型，則該類型不能跨元件界限使用。 跨越元件界限的範例包括從另一個元件呼叫方法，或從另一個元件中定義的型別衍生型別。
- 系統不會內嵌常數。
- <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> 類別不支援內嵌類型作為索引鍵。 您可以實作自己的字典類型，以支援索引鍵形式的內嵌類型。

## <a name="create-an-interface"></a>建立介面

第一個步驟是建立類型等價介面元件。 

1. 在 Visual Studio 中，選取 [檔案] > [新增] > [專案]。
   
1. 在 [**建立新專案**] 對話方塊的 [**搜尋範本**] 方塊中，輸入*類別庫*。 從清單中C#選取或 VB**類別庫（.NET Framework）** 範本，然後選取 **[下一步]** 。 
   
1. 在 [**設定您的新專案**] 對話方塊的 [**專案名稱**] 下，輸入*TypeEquivalenceInterface*，然後選取 [**建立**]。 隨即會建立新專案。
   
1. 在**方案總管**中，以滑鼠右鍵按一下*Class1.cs*或*Class1*檔案，選取 [**重新命名**]，然後將檔案從*Class1*重新命名為*ISampleInterface*。 在提示中回應 **[是]** ，也會將`ISampleInterface`類別重新命名為。 此類別代表類別的公用介面。
   
1. 在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceInterface**專案，然後選取 [**屬性**]。 
   
1. 在 [**屬性**] 畫面的左窗格中選取 [**建立**]，並將**輸出路徑**設定為您電腦上的位置，例如*C:\TypeEquivalenceSample*。 在本逐步解說中，您會使用相同的位置。 
   
1. 在 [**屬性**] 畫面的左窗格中選取 [**簽署**]，然後選取 [**簽署元件**] 核取方塊。 在 **[選擇強式名稱金鑰**檔] 的下拉式清單中，選取 [**新增**]。 
   
1. 在 [**建立強式名稱金鑰**] 對話方塊中的 [**金鑰檔名稱**] 下，輸入 [*金鑰 .snk*]。 取消選取 [**以密碼保護我的金鑰**檔] 核取方塊，然後選取 **[確定]** 。
   
1. 在程式碼編輯器中開啟*ISampleInterface*類別檔案，並以下列程式碼取代其內容以建立`ISampleInterface`介面：
   
   ```csharp
   using System;
   using System.Runtime.InteropServices;
   
   namespace TypeEquivalenceInterface
   {
       [ComImport]
       [Guid("8DA56996-A151-4136-B474-32784559F6DF")]
       public interface ISampleInterface
       {
           void GetUserInput();
           string UserInput { get; }
       }
   }
   ```
   
   ```vb
   Imports System.Runtime.InteropServices
   
   <ComImport()>
   <Guid("8DA56996-A151-4136-B474-32784559F6DF")>
   Public Interface ISampleInterface
       Sub GetUserInput()
       ReadOnly Property UserInput As String
   End Interface
   ```
   
1. 在 [**工具**] 功能表上，選取 [**建立 guid**]，然後在 [**建立 guid** ] 對話方塊中，選取 [登錄**格式**]。 選取 [**複製**]，然後選取 [結束 **]。**
   
1. 在您`Guid`程式碼的屬性中，以您複製的 guid 取代範例 guid，並移除大括弧（ **{}** ）。
   
1. 在**方案總管**中，展開 [**屬性**] 資料夾，然後選取 [ *AssemblyInfo.cs* ] 或 [ *AssemblyInfo* ] 檔案。 在 [程式碼編輯器] 中，將下列屬性新增至檔案：
   
   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```
   
   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```
   
1. + +選取 [檔案] [全部儲存] 或按 Ctrl Shift S 以儲存檔案和專案。 > 
   
1. 在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceInterface**專案，然後選取 [**建立**]。 類別庫 DLL 檔案會經過編譯並儲存到指定的組建輸出路徑，例如*C:\TypeEquivalenceSample*。

## <a name="create-a-runtime-class"></a>建立執行時間類別

接下來，建立類型等價執行時間類別。

1. 在 Visual Studio 中，選取 [檔案] > [新增] > [專案]。
   
1. 在 [**建立新專案**] 對話方塊的 [**搜尋範本**] 方塊中，輸入*類別庫*。 從清單中C#選取或 VB**類別庫（.NET Framework）** 範本，然後選取 **[下一步]** 。 
   
1. 在 [**設定您的新專案**] 對話方塊的 [**專案名稱**] 下，輸入*TypeEquivalenceRuntime*，然後選取 [**建立**]。 隨即會建立新專案。
   
1. 在**方案總管**中，以滑鼠右鍵按一下*Class1.cs*或*Class1*檔案，選取 [**重新命名**]，然後將檔案從*Class1*重新命名為*SampleClass*。 在提示中回應 **[是]** ，也會將`SampleClass`類別重新命名為。 這個類別會實作 `ISampleInterface` 介面。
   
1. 在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceInterface**專案，然後選取 [**屬性**]。 
   
1. 在 [**屬性**] 畫面的左窗格中選取 [**建立**]，然後將**輸出路徑**設定為您用於 TypeEquivalenceInterface 專案的相同位置，例如*C:\TypeEquivalenceSample*。
   
1. 在 [**屬性**] 畫面的左窗格中選取 [**簽署**]，然後選取 [**簽署元件**] 核取方塊。 在 **[選擇強式名稱金鑰**檔] 的下拉式清單中，選取 [**新增**]。 
   
1. 在 [**建立強式名稱金鑰**] 對話方塊中的 [**金鑰檔名稱**] 下，輸入 [*金鑰 .snk*]。 取消選取 [**以密碼保護我的金鑰**檔] 核取方塊，然後選取 **[確定]** 。
   
1. 在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceRuntime**專案，然後選取 [**加入** > **參考**]。 
   
1. 在 [**參考管理員**] 對話方塊中，選取 **[流覽**] 並流覽至 [輸出路徑] 資料夾。 選取 [ *TypeEquivalenceInterface* ] 檔案，選取 [**新增**]，然後選取 **[確定]** 。
   
1. 在**方案總管**中，展開 [**參考**] 資料夾，然後選取 [ **TypeEquivalenceInterface** ] 參考。 在 [**屬性**] 窗格中，將 [**特定版本**] 設為 [ **False** ] （如果尚未設定）。
   
1. 在程式碼編輯器中開啟*SampleClass*類別檔案，並以下列程式碼取代其內容，以建立`SampleClass`類別：
   
   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
   using TypeEquivalenceInterface;
   
   namespace TypeEquivalenceRuntime
   {
       public class SampleClass : ISampleInterface
       {
           private string p_UserInput;
           public string UserInput { get { return p_UserInput; } }
   
           public void GetUserInput()
           {
               Console.WriteLine("Please enter a value:");
               p_UserInput = Console.ReadLine();
           }
       }
   }
   ```
   
   ```vb
   Imports TypeEquivalenceInterface
   
   Public Class SampleClass
       Implements ISampleInterface
   
       Private p_UserInput As String
       Public ReadOnly Property UserInput() As String Implements ISampleInterface.UserInput
           Get
               Return p_UserInput
           End Get
       End Property
   
       Public Sub GetUserInput() Implements ISampleInterface.GetUserInput
           Console.WriteLine("Please enter a value:")
           p_UserInput = Console.ReadLine()
       End Sub
   End Class
   ```
   
1. + +選取 [檔案] [全部儲存] 或按 Ctrl Shift S 以儲存檔案和專案。 > 
   
1. 在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceRuntime**專案，然後選取 [**建立**]。 類別庫 DLL 檔案會經過編譯並儲存到指定的組建輸出路徑。

## <a name="create-a-client-project"></a>建立用戶端專案

最後，建立參考介面元件的類型等價用戶端程式。

1. 在 Visual Studio 中，選取 [檔案] > [新增] > [專案]。
   
1. 在 [**建立新專案**] 對話方塊的 [**搜尋範本**] 方塊中，輸入*console* 。 從清單中C#選取 [或 VB**主控台應用程式（.NET Framework）** ] 範本，然後選取 **[下一步]** 。 
   
1. 在 [**設定您的新專案**] 對話方塊的 [**專案名稱**] 下，輸入*TypeEquivalenceClient*，然後選取 [**建立**]。 隨即會建立新專案。
   
1. 在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceClient**專案，然後選取 [**屬性**]。 
   
1. 在 [**屬性**] 畫面的左窗格中選取 [**建立**]，然後將**輸出路徑**設定為您用於 TypeEquivalenceInterface 專案的相同位置，例如*C:\TypeEquivalenceSample*。
   
1. 在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceClient**專案，然後選取 [**加入** > **參考**]。 
   
1. 在 [**參考管理員**] 對話方塊中，如果已列出 [ **TypeEquivalenceInterface** ] 檔案，請選取它。 如果沒有，請選取 **[流覽]** ，流覽至 [輸出路徑] 資料夾，選取 [ *TypeEquivalenceInterface* ] 檔案（而非*TypeEquivalenceRuntime*），然後選取 [**新增**]。 選取 [確定]。
   
1. 在**方案總管**中，展開 [**參考**] 資料夾，然後選取 [ **TypeEquivalenceInterface** ] 參考。 在 [**屬性**] 窗格中，將 [**內嵌 Interop 類型**] 設定為 [ **True**]。
   
1. 在程式碼編輯器中開啟*Program.cs*或*Module1*檔案，並以下列程式碼取代其內容，以建立用戶端程式：
   
   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
   using TypeEquivalenceInterface;
   using System.Reflection;
   
   namespace TypeEquivalenceClient
   {
       class Program
       {
           static void Main(string[] args)
           {
               Assembly sampleAssembly = Assembly.Load("TypeEquivalenceRuntime");
               ISampleInterface sampleClass =
                   (ISampleInterface)sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass");
               sampleClass.GetUserInput();
               Console.WriteLine(sampleClass.UserInput);
               Console.WriteLine(sampleAssembly.GetName().Version.ToString());
               Console.ReadLine();
           }
       }
   }
   ```
   
   ```vb
   Imports TypeEquivalenceInterface
   Imports System.Reflection
   
   Module Module1
   
       Sub Main()
           Dim sampleAssembly = Assembly.Load("TypeEquivalenceRuntime")
           Dim sampleClass As ISampleInterface = CType( _
               sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass"), ISampleInterface)
           sampleClass.GetUserInput()
           Console.WriteLine(sampleClass.UserInput)
           Console.WriteLine(sampleAssembly.GetName().Version)
           Console.ReadLine()
       End Sub
   
   End Module
   ```
   
1. + +選取 [檔案] [全部儲存] 或按 Ctrl Shift S 以儲存檔案和專案。 > 
   
1. 按**Ctrl** + **F5**以建立並執行程式。 請注意，主控台輸出會傳回元件版本**1.0.0.0**。 
   
## <a name="modify-the-interface"></a>修改介面

現在，修改介面元件，並變更其版本。 

1. 在 Visual Studio 中，**選取** > [檔案] [**開啟** > **專案/方案**]，然後開啟 [ **TypeEquivalenceInterface** ] 專案。
   
1. 在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceInterface**專案，然後選取 [**屬性**]。 
   
1. 在 [**屬性**] 畫面的左窗格中選取 [**應用程式**]，然後選取 [**元件資訊**]。 
   
1. 在 [**元件資訊**] 對話方塊中，將 [**元件版本**] 和 [檔案**版本**] 值變更為*2.0.0.0*，然後選取 **[確定]** 。
   
1. 開啟*SampleInterface.cs*或*SampleInterface*檔案，然後將下列程式`ISampleInterface`程式碼新增至介面：
   
   ```csharp
   DateTime GetDate();
   ```
   
   ```vb
   Function GetDate() As Date
   ```
   
1. + +選取 [檔案] [全部儲存] 或按 Ctrl Shift S 以儲存檔案和專案。 > 
   
1. 在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceInterface**專案，然後選取 [**建立**]。 類別庫 DLL 檔案的新版本會進行編譯，並儲存至組建輸出路徑。

## <a name="modify-the-runtime-class"></a>修改執行時間類別

同時修改執行時間類別並更新其版本。 

1. 在 Visual Studio 中，**選取** > [檔案] [**開啟** > **專案/方案**]，然後開啟 [ **TypeEquivalenceRuntime** ] 專案。
   
1. 在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceRuntime**專案，然後選取 [**屬性**]。 
   
1. 在 [**屬性**] 畫面的左窗格中選取 [**應用程式**]，然後選取 [**元件資訊**]。 
   
1. 在 [**元件資訊**] 對話方塊中，將 [**元件版本**] 和 [檔案**版本**] 值變更為*2.0.0.0*，然後選取 **[確定]** 。
   
1. 開啟*SampleClass.cs*或*SampleClass*檔案，然後將下列程式`SampleClass`代碼新增至類別：
   
   ```csharp
    public DateTime GetDate()
    {
        return DateTime.Now;
    }
   ```
   
   ```vb
   Public Function GetDate() As DateTime Implements ISampleInterface.GetDate
       Return Now
   End Function
   ```
   
1. + +選取 [檔案] [全部儲存] 或按 Ctrl Shift S 以儲存檔案和專案。 > 
   
1. 在**方案總管**中，以滑鼠右鍵按一下**TypeEquivalenceRuntime**專案，然後選取 [**建立**]。 類別庫 DLL 檔案的新版本會進行編譯，並儲存至組建輸出路徑。

## <a name="run-the-updated-client-program"></a>執行更新的用戶端程式 

移至組建輸出檔案夾位置，並執行*TypeEquivalenceClient*。 請注意，主控台輸出現在會反映新版本的`TypeEquivalenceRuntime`元件*2.0.0.0*，而不會重新編譯程式。

## <a name="see-also"></a>另請參閱

- [/link (C# 編譯器選項)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
- [C# 程式設計指南](../../csharp/programming-guide/index.md)
- [程式設計概念（Visual Basic）](../../visual-basic/programming-guide/concepts/index.md)
- [具有元件的程式](program.md)
- [.NET 中的組件](index.md)
