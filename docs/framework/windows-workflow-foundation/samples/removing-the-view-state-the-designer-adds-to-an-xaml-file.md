---
title: 移除設計工具加入至 XAML 檔案的檢視狀態-WF
ms.date: 03/30/2017
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
ms.openlocfilehash: f431275140e821aa5ec4d2235322f06be87d5ee2
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715614"
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a>移除設計工具加入至 XAML 檔案的檢視狀態

此範例示範如何建立衍生自 <xref:System.Xaml.XamlWriter> 的類別，以及從 XAML 檔案移除檢視狀態。 Windows 工作流程設計工具會將資訊寫入 XAML 檔，這稱為「檢視狀態」。 檢視狀態是指設計階段必要的資訊，例如執行階段不需要的版面配置定位。 工作流程設計工具在編輯 XAML 檔時，將此資訊插入其中。 工作流程設計工具會將檢視狀態寫入具有 `mc:Ignorable` 屬性的 XAML 檔案中，因此當執行時間載入 XAML 檔案時，不會載入此資訊。 這個範例示範如何在處理 XAML 節點時建立可移除檢視狀態資訊的類別。

## <a name="discussion"></a>討論

這個範例示範如何建立自訂寫入器。

若要建置自訂的 XAML 寫入器，請建立繼承自 <xref:System.Xaml.XamlWriter> 的類別。 由於 XAML 寫入器通常是嵌套的，因此通常會追蹤「內部」 XAML 撰寫程式。 這些「內部」寫入器可視為 XAML 寫入器其餘堆疊的參考，可讓您擁有多個進入點來執行工作，然後將處理委派給堆疊的其餘部分。

在這個範例中有數個值得注意的項目。 一個是正在寫入的項目是否來自設計工具命名空間的檢查。 請注意，這同時也會將工作流程中設計工具命名空間的其他類型用法刪除。

```csharp
static Boolean IsDesignerAttachedProperty(XamlMember xamlMember)
{
    return xamlMember.IsAttachable &&
        xamlMember.PreferredXamlNamespace.Equals(c_sapNamespaceURI, StringComparison.OrdinalIgnoreCase);
}

const String c_sapNamespaceURI = "http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation";

// The next item of interest is the constructor, where the utilization of the inner XAML writer is seen.
public ViewStateCleaningWriter(XamlWriter innerWriter)
{
    this.InnerWriter = innerWriter;
    this.MemberStack = new Stack<XamlMember>();
}

XamlWriter InnerWriter {get; set; }
Stack<XamlMember> MemberStack {get; set; }
```

這也會建立周遊節點資料流時所用的 XAML 成員堆疊。 這個範例的其餘部分大多是包含在 `WriteStartMember` 方法中。

```csharp
public override void WriteStartMember(XamlMember xamlMember)
{
    MemberStack.Push(xamlMember);

    if (IsDesignerAttachedProperty(xamlMember))
    {
        m_attachedPropertyDepth++;
    }

    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteStartMember(xamlMember);
}
```

後續方法接著檢查它們是否仍包含在檢視狀態容器中，如果是的話則返回，而不會在寫入器堆疊向下傳遞節點。

```csharp
public override void WriteValue(Object value)
{
    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteValue(value);
}
```

若要使用自訂 XAML 寫入器，您必須將它鏈結在 XAML 寫入器堆疊中。 下列程式碼示範這個使用方式。

```csharp
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);
```

## <a name="to-use-this-sample"></a>若要使用這個範例

1. 使用 Visual Studio 2010，開啟 [Viewstatecleaningwriter.exe] 方案檔。

2. 開啟命令提示字元，然後巡覽到建置 ViewStageCleaningWriter.exe 的目錄。

3. 對 Workflow1.xaml 檔案執行 ViewStateCleaningWriter.exe。

   下列範例示範此可執行檔的語法。

   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```

   這會將 XAML 檔案輸出至 \[outfile]，並移除其所有檢視狀態資訊。

> [!NOTE]
> <xref:System.Activities.Statements.Sequence> 工作流程的數個虛擬化提示會被移除。 這樣會導致設計工具下次載入時重新計算配置。 對 <xref:System.Activities.Statements.Flowchart> 使用這個範例時，所有定位和線條路由資訊都會被移除，在設計工具後續載入時，所有活動都會堆疊在畫面左側。

## <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a>若要建立這個範例所用的範例 XAML 檔案

1. 開啟 Visual Studio 2010。

2. 建立新的工作流程主控台應用程式。

3. 將數個活動拖放到畫布上。

4. 儲存工作流程 XAML 檔案。

5. 檢查 XAML 檔案是否有檢視狀態附加屬性。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
