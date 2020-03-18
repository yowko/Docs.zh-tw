---
title: 演練：在視覺化工作室中嵌入來自託管程式集的類型
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: f11fbedad766753ee462c5f597b823493cdaf7cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "75338548"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a>演練：在視覺化工作室中嵌入來自託管程式集的類型

若要內嵌來自強式名稱 Managed 組件的類型資訊，您可以鬆散地結合應用程式中的類型以確保版本獨立。 也就是說，可以將程式編寫為使用託管庫任何版本的類型，而無需為每個新版本重新編譯。

內嵌型別時，通常會搭配使用 COM Interop (例如從 Microsoft Office 使用 Automation 物件的應用程式)。 當您內嵌類型資訊時，可讓相同組建的程式使用不同電腦上版本各異的 Microsoft Office。 但是，您也可以將類型嵌入與完全託管的解決方案一起使用。

指定可以嵌入的公共介面後，將創建實現這些介面的運行時類。 用戶端程式可以通過引用包含公共介面的程式集並設置`Embed Interop Types`引用`True`的屬性來在設計時嵌入介面的類型資訊。 然後，用戶端程式可以載入作為這些介面鍵入的運行時物件的實例。 這相當於使用命令列編譯器並使用[-link 編譯器選項](../../csharp/language-reference/compiler-options/link-compiler-option.md)引用程式集。

如果創建強命名的運行時程式集的新版本，則不必重新編譯用戶端程式。 用戶端程式繼續使用任何可用的運行時程式集版本，使用公共介面的嵌入式類型資訊。

在本逐步解說中，您將：

1. 創建具有公共介面的強命名程式集，其中包含可嵌入的類型資訊。
1. 創建實現公共介面的強命名運行時程式集。
1. 建立用戶端程式，以內嵌公用介面的類型資訊，並從執行階段組件建立類別的執行個體。
1. 修改並重新建置執行階段組件。
1. 運行用戶端程式以查看它使用新版本的運行時程式集，而無需重新編譯。

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a>條件和限制

您可以在以下條件下嵌入程式集中的類型資訊：

- 組件已公開至少一個公用介面。
- 嵌入介面用`ComImport`具有唯一 GUID 的屬性`Guid`和屬性進行帶子。
- 您可以使用 `ImportedFromTypeLib` 屬性或 `PrimaryInteropAssembly` 屬性及組件層級 `Guid` 屬性，來標註組件  預設情況下，Visual C# 和 Visual Basic 專案範本`Guid`包括程式集級屬性。

由於類型嵌入的主要功能是支援 COM 交互操作程式集，因此在完全託管的解決方案中嵌入類型資訊時，以下限制適用：

- 僅嵌入特定于 COM 交互操作的屬性。 其他屬性將被忽略。
- 如果類型使用泛型參數，並且泛型參數的類型是嵌入類型，則無法跨程式集邊界使用該類型。 跨越程式集邊界的示例包括從另一個程式集調用方法或從另一個程式集中定義的類型派生類型。
- 系統不會內嵌常數。
- <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> 類別不支援內嵌類型作為索引鍵。 您可以實作自己的字典類型，以支援索引鍵形式的內嵌類型。

## <a name="create-an-interface"></a>建立介面

第一步是創建類型等效介面程式集。

1. 在視覺化工作室中，選擇 **"檔** > **新專案** > **"。**

1. 在"**創建新專案**"對話方塊中，在 **"搜索範本"** 框中鍵入*類庫*。 從清單中選擇 C# 或視覺化基本**類庫 （.NET 框架）** 範本，然後選擇 **"下一步**"。

1. 在 **"配置新專案**"對話方塊中，在**專案名稱**下鍵入*TypeValvalence 介面*，然後選擇"**創建**"。 隨即建立新專案。

1. 在**解決方案資源管理器**中，按右鍵*Class1.cs*或*Class1.vb*檔，選擇**重命名**，並將檔從*類 1*重命名到*ISampleInterface*。 回應 **"是**"的提示，將類重命名為`ISampleInterface`。 此類表示類的公共介面。

1. 在**解決方案資源管理器**中，按右鍵**TypeValence 介面**專案，然後選擇**屬性**。

1. 選擇 **"在****屬性"** 螢幕左窗格上的"生成"，並將 **"輸出"路徑**設置為電腦上的位置，例如*C：_TypeValenceSample*。 在本演練中，您使用相同的位置。

1. 選擇 **"屬性"** 螢幕左側窗格上的 **"簽名**"，然後選擇"**對程式集進行簽名**"核取方塊。 在 **"選擇強式名稱金鑰檔**"的下拉清單中，選擇 **"新建**"。

1. 在 **"創建強式名稱鍵**"對話方塊中，在**鍵檔案名**下鍵入*key.snk*。 取消選中 **"使用密碼核取方塊保護我的金鑰檔**"，然後選擇 **"確定**"。

1. 在代碼編輯器中打開*ISampleInterface*類檔，並將其內容替換為以下代碼以創建`ISampleInterface`介面：

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

1. 在 **"工具"** 功能表上，**選擇"創建 Guid**"，在 **"創建 GUID"** 對話方塊中，選擇 **"註冊表格式**"。 選擇 **"複製**"，然後選擇 **"退出**"。

1. 在`Guid`代碼的屬性中，將示例 GUID 替換為複製的 GUID，然後刪除大括弧 **（***）。

1. 在**解決方案資源管理器**中，展開**屬性**資料夾並選擇*AssemblyInfo.cs*或*AssemblyInfo.vb*檔。 在代碼編輯器中，向檔添加以下屬性：

   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```

   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```

1. 選擇 **"全部** > **保存**檔"或按**Ctrl**+**Shift**+**S**以保存檔和專案。

1. 在**解決方案資源管理器**中，按右鍵**TypeValence 介面**專案並選擇 **"生成**"。 類庫 DLL 檔被編譯並保存到指定的生成輸出路徑，例如*C：_TypeEquivalenceSample*。

## <a name="create-a-runtime-class"></a>創建運行時類

接下來，創建類型等效運行時類。

1. 在視覺化工作室中，選擇 **"檔** > **新專案** > **"。**

1. 在"**創建新專案**"對話方塊中，在 **"搜索範本"** 框中鍵入*類庫*。 從清單中選擇 C# 或視覺化基本**類庫 （.NET 框架）** 範本，然後選擇 **"下一步**"。

1. 在"**配置新專案**"對話方塊中，在 **"專案名稱**"下鍵入*TypeValvalence 執行時間*，然後選擇"**創建**"。 隨即建立新專案。

1. 在**解決方案資源管理器**中，按右鍵*Class1.cs*或*Class1.vb*檔，選擇 **"重命名**"並將檔從*類 1*重命名到*示例類*。 回應 **"是**"的提示，將類重命名為`SampleClass`。 此類別會實作 `ISampleInterface` 介面。

1. 在**解決方案資源管理器中**，按右鍵**TypeValence 介面**專案並選擇**屬性**。

1. 選擇"**屬性"** 螢幕左窗格上的 **"生成****"，然後將"輸出"路徑**設置為與 TypeEquivalence 介面專案所用的相同位置，例如*C：_TypeEquivalenceSample*。

1. 選擇 **"屬性"** 螢幕左側窗格上的 **"簽名**"，然後選擇"**對程式集進行簽名**"核取方塊。 在 **"選擇強式名稱金鑰檔**"的下拉清單中，選擇 **"新建**"。

1. 在 **"創建強式名稱鍵**"對話方塊中，在**鍵檔案名**下鍵入*key.snk*。 取消選中 **"使用密碼核取方塊保護我的金鑰檔**"，然後選擇 **"確定**"。

1. 在**解決方案資源管理器中**，按右鍵 **"類型等效執行時間"** 專案，然後選擇"**添加** > **參考**"。

1. 在 **"參考管理器"** 對話方塊中，選擇 **"流覽**"並流覽到輸出路徑資料夾。 選擇*TypeValenceInterface.dll*檔，選擇 **"添加**"，然後選擇 **"確定**"。

1. 在**解決方案資源管理器**中，展開**引用**資料夾並選擇**類型等效介面**引用。 在"**屬性"** 窗格中，將 **"特定版本**"設置為 **"false"（** 如果尚未）。

1. 在代碼編輯器中打開*Sampleclass*類檔，並將其內容替換為以下代碼以創建類`SampleClass`：

   ```csharp
   using System;
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

1. 選擇 **"全部** > **保存**檔"或按**Ctrl**+**Shift**+**S**以保存檔和專案。

1. 在**解決方案資源管理器**中，按右鍵 **"類型等效執行時間**"專案並選擇 **"生成**"。 類庫 DLL 檔被編譯並保存到指定的生成輸出路徑。

## <a name="create-a-client-project"></a>創建用戶端專案

最後，創建引用介面程式集的類型等效用戶端程式。

1. 在視覺化工作室中，選擇 **"檔** > **新專案** > **"。**

1. 在"**創建新專案**"對話方塊中，在 **"搜索範本"** 框中鍵入*主控台*。 從清單中選擇 C# 或視覺化基本**主控台應用 （.NET 框架）** 範本，然後選擇 **"下一步**"。

1. 在"**配置新專案**"對話方塊中，在**專案名稱**下鍵入*TypeValvalence 用戶端*，然後選擇"**創建**"。 隨即建立新專案。

1. 在**解決方案資源管理器中**，按右鍵**TypeValenceClient**專案並選擇**屬性**。

1. 選擇"**屬性"** 螢幕左窗格上的 **"生成****"，然後將"輸出"路徑**設置為與 TypeEquivalence 介面專案所用的相同位置，例如*C：_TypeEquivalenceSample*。

1. 在**解決方案資源管理器中**，按右鍵**TypeValenceClient**專案並選擇"**添加** > **參考**"。

1. 在**參考管理器**對話方塊中，如果已列出**TypeEquivalenceInterface.dll**檔，請選擇它。 如果沒有，請選擇 **"流覽**"，流覽到輸出路徑資料夾，選擇*TypeEquivalenceInterface.dll*檔（不是*TypeValenceruntime.dll），* 然後選擇"**添加**"。 選取 [確定]****。

1. 在**解決方案資源管理器**中，展開**引用**資料夾並選擇**類型等效介面**引用。 在"**屬性"** 窗格中，將 **"嵌入互通類型"** 設置為 **"true"。**

1. 在代碼編輯器中打開*Program.cs*或*Module1.vb*檔，並將其內容替換為以下代碼以創建用戶端程式：

   ```csharp
   using System;
   using System.Reflection;
   using TypeEquivalenceInterface;

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
   Imports System.Reflection
   Imports TypeEquivalenceInterface

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

1. 選擇 **"全部** > **保存**檔"或按**Ctrl**+**Shift**+**S**以保存檔和專案。

1. 按**Ctrl**+**F5**生成並運行程式。 請注意，主控台輸出返回程式集版本**1.0.0.0**。

## <a name="modify-the-interface"></a>修改介面

現在，修改介面程式集，並更改其版本。

1. 在視覺化工作室中，選擇 **"檔** > **打開** > **專案/解決方案**"，然後打開**類型等效介面**專案。

1. 在**解決方案資源管理器中**，按右鍵**TypeValence 介面**專案並選擇**屬性**。

1. 在 **"屬性"** 螢幕的左側窗格中選擇 **"應用程式**"，然後選擇 **"程式集資訊**"。

1. 在 **"程式集資訊"** 對話方塊中，將**程式集版本**和**檔版本**值更改為*2.0.0.0*，然後選擇 **"確定**"。

1. 打開*SampleInterface.cs*或*示例介面.vb*檔，並將以下程式碼添加到`ISampleInterface`介面：

   ```csharp
   DateTime GetDate();
   ```

   ```vb
   Function GetDate() As Date
   ```

1. 選擇 **"全部** > **保存**檔"或按**Ctrl**+**Shift**+**S**以保存檔和專案。

1. 在**解決方案資源管理器**中，按右鍵**TypeValence 介面**專案並選擇 **"生成**"。 編譯類庫 DLL 檔的新版本並將其保存到生成輸出路徑。

## <a name="modify-the-runtime-class"></a>修改運行時類

還要修改運行時類並更新其版本。

1. 在視覺化工作室中，選擇 **"檔** > **打開** > **專案/解決方案**"，然後打開**TypeValenceRuntime**專案。

1. 在**解決方案資源管理器中**，按右鍵**TypeValence 運行時**專案並選擇**屬性**。

1. 在 **"屬性"** 螢幕的左側窗格中選擇 **"應用程式**"，然後選擇 **"程式集資訊**"。

1. 在 **"程式集資訊"** 對話方塊中，將**程式集版本**和**檔版本**值更改為*2.0.0.0*，然後選擇 **"確定**"。

1. 打開*SampleClass.cs*或*sampleClass.vb*檔，並將以下代碼添加到`SampleClass`類：

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

1. 選擇 **"全部** > **保存**檔"或按**Ctrl**+**Shift**+**S**以保存檔和專案。

1. 在**解決方案資源管理器**中，按右鍵 **"類型等效執行時間**"專案並選擇 **"生成**"。 編譯類庫 DLL 檔的新版本並將其保存到生成輸出路徑。

## <a name="run-the-updated-client-program"></a>運行更新的用戶端程式

轉到生成輸出檔案夾位置並運行*TypeEquivalenceClient.exe*。 請注意，主控台輸出現在反映`TypeEquivalenceRuntime`程式集的新版本*2.0.0.0，* 無需重新編譯程式。

## <a name="see-also"></a>另請參閱

- [-link (C# 編譯器選項)](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [-連結（視覺基礎）](../../visual-basic/reference/command-line-compiler/link.md)
- [C# 程式設計指南](../../csharp/programming-guide/index.md)
- [程式設計概念（視覺基礎）](../../visual-basic/programming-guide/concepts/index.md)
- [.NET 中的組件](index.md)
