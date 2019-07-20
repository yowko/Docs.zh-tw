---
title: ToolStrip 控制項架構
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], architecture
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
ms.openlocfilehash: d0a1441e9bae8d2c1f938e7399c11e736708da4d
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363834"
---
# <a name="toolstrip-control-architecture"></a>ToolStrip 控制項架構

<xref:System.Windows.Forms.ToolStrip> 和<xref:System.Windows.Forms.ToolStripItem>類別提供彈性、可擴充的系統, 以顯示工具列、狀態和功能表項目。 這些類別全都包含在<xref:System.Windows.Forms>命名空間中, 而且通常會以 "ToolStrip" 前置詞 ( <xref:System.Windows.Forms.ToolStripOverflow>例如) 或 "寬頻<xref:System.Windows.Forms.MenuStrip>" 尾碼 (例如) 命名。

## <a name="toolstrip"></a>ToolStrip

下列主題描述<xref:System.Windows.Forms.ToolStrip>和衍生自它的控制項。

<xref:System.Windows.Forms.ToolStrip>是<xref:System.Windows.Forms.MenuStrip>、 <xref:System.Windows.Forms.StatusStrip>和的抽象基類。<xref:System.Windows.Forms.ContextMenuStrip> 下列物件模型會顯示<xref:System.Windows.Forms.ToolStrip>繼承階層架構。

![顯示 ToolStrip 物件模型的圖表。](./media/toolstrip-control-architecture/toolstrip-object-model.gif)

您可以<xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ToolStrip.Items%2A>透過集合存取中的所有專案。 您可以<xref:System.Windows.Forms.ToolStripDropDownItem> <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A>透過集合存取中的所有專案。 在衍生自<xref:System.Windows.Forms.ToolStrip>的類別中, 您也可以<xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A>使用屬性來存取目前顯示的專案。 這些是目前不在溢位功能表中的專案。

下列專案是特別設計來與所有方向的和<xref:System.Windows.Forms.ToolStripSystemRenderer> <xref:System.Windows.Forms.ToolStripProfessionalRenderer>同時順暢地搭配使用。 根據預設, 這些<xref:System.Windows.Forms.ToolStrip>控制項在設計階段可供使用:

- <xref:System.Windows.Forms.ToolStripButton>

- <xref:System.Windows.Forms.ToolStripSeparator>

- <xref:System.Windows.Forms.ToolStripLabel>

- <xref:System.Windows.Forms.ToolStripDropDownButton>

- <xref:System.Windows.Forms.ToolStripSplitButton>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="menustrip"></a>MenuStrip

<xref:System.Windows.Forms.MenuStrip>是取代<xref:System.Windows.Forms.MainMenu>的最上層容器。 它也提供主要處理和多重文件介面 (MDI) 功能。 <xref:System.Windows.Forms.ToolStripDropDownItem>功能和<xref:System.Windows.Forms.ToolStripMenuItem>與<xref:System.Windows.Forms.ToolStripItem>一起使用, 但它們是衍生自。 <xref:System.Windows.Forms.MenuStrip>

下列專案是特別設計來與所有方向的和<xref:System.Windows.Forms.ToolStripSystemRenderer> <xref:System.Windows.Forms.ToolStripProfessionalRenderer>同時順暢地搭配使用。 根據預設, 這些<xref:System.Windows.Forms.MenuStrip>控制項在設計階段可供使用:

- <xref:System.Windows.Forms.ToolStripMenuItem>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="statusstrip"></a>StatusStrip

<xref:System.Windows.Forms.StatusStrip><xref:System.Windows.Forms.StatusBar>取代控制項。 的<xref:System.Windows.Forms.StatusStrip>特殊功能包括自訂資料表配置、支援表單的調整大小和移動掌握, `Spring`以及屬性, 讓能夠自動<xref:System.Windows.Forms.ToolStripStatusLabel>填滿可用的空間。

下列專案是特別設計來與所有方向的和<xref:System.Windows.Forms.ToolStripSystemRenderer> <xref:System.Windows.Forms.ToolStripProfessionalRenderer>同時順暢地搭配使用。 根據預設, 這些<xref:System.Windows.Forms.StatusStrip>控制項在設計階段可供使用:

- <xref:System.Windows.Forms.ToolStripStatusLabel>

- <xref:System.Windows.Forms.ToolStripDropDownButton>

- <xref:System.Windows.Forms.ToolStripSplitButton>

- <xref:System.Windows.Forms.ToolStripProgressBar>

### <a name="contextmenustrip"></a>ContextMenuStrip

<xref:System.Windows.Forms.ContextMenuStrip> 會取代 <xref:System.Windows.Forms.ContextMenu>。 您可以將<xref:System.Windows.Forms.ContextMenuStrip>與任何控制項產生關聯, 然後按一下滑鼠右鍵, 就會自動顯示內容功能表 (或快捷方式功能表)。 您可以<xref:System.Windows.Forms.ContextMenuStrip> <xref:System.Windows.Forms.ToolStripDropDown.Show%2A>使用方法, 以程式設計方式顯示。 <xref:System.Windows.Forms.ContextMenuStrip>支援可取消<xref:System.Windows.Forms.ToolStripDropDown.Closing>和事件來處理動態擴展和多點按的案例。 <xref:System.Windows.Forms.ToolStripDropDown.Opening> <xref:System.Windows.Forms.ContextMenuStrip>支援影像、功能表項目檢查狀態、文字、存取金鑰、快捷方式和串聯功能表。

下列專案是特別設計來與所有方向的和<xref:System.Windows.Forms.ToolStripSystemRenderer> <xref:System.Windows.Forms.ToolStripProfessionalRenderer>同時順暢地搭配使用。 根據預設, 這些<xref:System.Windows.Forms.ContextMenuStrip>控制項在設計階段可供使用:

- <xref:System.Windows.Forms.ToolStripMenuItem>

- <xref:System.Windows.Forms.ToolStripSeparator>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="toolstrip-generic-features"></a>ToolStrip 一般功能

下列主題描述<xref:System.Windows.Forms.ToolStrip>和衍生控制項的泛型功能與行為。

#### <a name="painting"></a>進行

您可以透過數種方式<xref:System.Windows.Forms.ToolStrip>在控制項中執行自訂繪製。 <xref:System.Windows.Forms.ToolStrip>和其他 Windows Forms 控制項一樣, 和<xref:System.Windows.Forms.ToolStripItem>都具有可覆`OnPaint`寫的`Paint`方法和事件。 如同一般繪製, 座標系統是相對於控制項的工作區;也就是說, 控制項的左上角為 0, 0。 的事件和`OnPaint` 方法<xref:System.Windows.Forms.ToolStripItem>的行為就像其他控制項繪製事件一樣。 `Paint`

控制項也可以<xref:System.Windows.Forms.ToolStripRenderer>透過類別提供更細微的方式來呈現專案和容器, 其具有可覆寫的方法來繪製背景、專案背景、專案影像、專案箭號、專案文字, 以及的框線。 <xref:System.Windows.Forms.ToolStrip><xref:System.Windows.Forms.ToolStrip>. 這些方法的事件引數會公開數個屬性, 例如您可以視需要調整的矩形、色彩和文字格式。

若只要調整專案繪製方式的幾個層面, 通常會覆寫<xref:System.Windows.Forms.ToolStripRenderer>。

如果您要撰寫新的專案, 並且想要控制繪製的所有層面, 請覆`OnPaint`寫方法。 在中`OnPaint`, 您可以使用的<xref:System.Windows.Forms.ToolStripRenderer>方法。

根據預設, <xref:System.Windows.Forms.ToolStrip>會進行雙重緩衝處理, 利用<xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer>設定。

#### <a name="parenting"></a>設父代

容器擁有權和父代的概念在控制項中<xref:System.Windows.Forms.ToolStrip>比其他 Windows Forms 的容器控制項更為複雜。 這是支援動態案例 (例如溢位、跨多個<xref:System.Windows.Forms.ToolStrip>專案共用下拉式專案, 以及支援<xref:System.Windows.Forms.ContextMenuStrip>從控制項產生) 所需的。

下列清單描述與父代相關的成員, 並說明其用法。

- <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A>存取做為下拉式專案來源的專案。 這類似<xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>于, 但會傳回, 而不是傳回控制項<xref:System.Windows.Forms.ToolStripItem>。

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A><xref:System.Windows.Forms.ContextMenuStrip>當多個控制項共用相同<xref:System.Windows.Forms.ContextMenuStrip>的時, 決定哪個控制項是的來源。

- <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A>是<xref:System.Windows.Forms.ToolStripItem.Parent%2A>屬性的唯讀存取子。 父系與擁有者不同之處在于, 父系代表在其中顯示<xref:System.Windows.Forms.ToolStrip>專案的傳回目前, 這可能是在溢位區域中。

- <xref:System.Windows.Forms.ToolStripItem.Owner%2A>傳回, <xref:System.Windows.Forms.ToolStrip>其專案集合包含目前<xref:System.Windows.Forms.ToolStripItem>的。 這是在最上層參考<xref:System.Windows.Forms.ToolStrip.ImageList%2A>或其他屬性, <xref:System.Windows.Forms.ToolStrip>而不需要撰寫特殊程式碼來處理溢位的最佳方式。

#### <a name="behavior-of-inherited-controls"></a>繼承控制項的行為

當下列控制項用於繼承時, 就會鎖定:

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.ToolStripPanel>, 其中包括中<xref:System.Windows.Forms.ToolStripContainer>的面板, 以及個別<xref:System.Windows.Forms.ToolStripPanel>的控制項。

例如, 使用上一個清單中的一或多個控制項, 建立新的 Windows Forms 應用程式。 將一個或多個控制項的存取修飾詞`public`設定`protected`為或, 然後建立專案。 新增繼承自第一個表單的表單, 然後選取繼承的控制項。 控制項會顯示為已`private`鎖定, 其行為會如同其存取修飾詞一樣。

#### <a name="toolstripcontainer-support-of-inheritance"></a>ToolStripContainer 對繼承的支援

<xref:System.Windows.Forms.ToolStripContainer>控制項支援有限的繼承案例, 與下列範例類似:

1. 新建 Windows Forms 應用程式

2. 將 <xref:System.Windows.Forms.ToolStripContainer> 加入表單。

3. 將的存取修飾<xref:System.Windows.Forms.ToolStripContainer>詞設定為`public`或。 `protected`

4. 將<xref:System.Windows.Forms.ToolStrip>、 <xref:System.Windows.Forms.MenuStrip>和<xref:System.Windows.Forms.ToolStripPanel> <xref:System.Windows.Forms.ToolStripContainer>控制項的任意組合<xref:System.Windows.Forms.ContextMenuStrip>加入至的區域。

5. 建置專案。

6. 新增繼承自第一個表單的表單。

7. 選取表單<xref:System.Windows.Forms.ToolStripContainer>上的繼承。

#### <a name="inherited-behavior-of-child-controls"></a>子控制項的繼承行為

完成上述步驟之後, 會發生下列繼承的行為:

- 在設計工具中, 控制項會出現一個繼承的圖示。

- <xref:System.Windows.Forms.ToolStripPanel>控制項已鎖定; 您無法選取或重新排列其內容。

- 您可以將控制項<xref:System.Windows.Forms.ToolStripContentPanel>加入、移動控制項, 並將其設為的子控制項。 <xref:System.Windows.Forms.ToolStripContentPanel>

- 您的變更會在建立表單之後保存。

  > [!NOTE]
  > 從屬於一部分<xref:System.Windows.Forms.ToolStripPanel> <xref:System.Windows.Forms.ToolStripContainer>的所有控制項中移除存取修飾詞。 的存取修飾<xref:System.Windows.Forms.ToolStripContainer>詞會控管整個控制項。

#### <a name="partial-trust"></a>部分信任

在部分信任`ToolStrip`下的限制是為了避免不小心輸入可能由未經授權的人員或服務所使用的個人資訊而設計。 保護措施如下所示:

- `ToolStripDropDown`控制項需要<xref:System.Security.Permissions.UIPermissionWindow.AllWindows> <xref:System.Windows.Forms.ToolStripControlHost>在中顯示專案。 這適用于內部控制項 (例如<xref:System.Windows.Forms.ToolStripTextBox>、 <xref:System.Windows.Forms.ToolStripComboBox>和<xref:System.Windows.Forms.ToolStripProgressBar> ), 以及使用者建立的控制項。 如果不符合此需求, 則不會顯示這些專案。 不會有例外狀況擲回。

- 不允許將`false`屬性設定為, 而且會忽略可取消的事件參數。<xref:System.Windows.Forms.ToolStripDropDown.Closing> <xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A> 如此一來, 就無法在不關閉下拉式專案的情況下輸入多個按鍵。 如果不符合此需求, 則不會顯示這類專案。 不會有例外狀況擲回。

- 許多擊鍵處理事件若發生在以外的部分信任<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>內容中, 就不會引發。

- 未授與時<xref:System.Security.Permissions.UIPermissionWindow.AllWindows> , 不會處理存取金鑰。

#### <a name="usage"></a>使用量

下列使用模式具有<xref:System.Windows.Forms.ToolStrip>版面配置、鍵盤互動和使用者行為的關聯:

- 聯結于<xref:System.Windows.Forms.ToolStripPanel>

  可以在<xref:System.Windows.Forms.ToolStripPanel>和之間<xref:System.Windows.Forms.ToolStripPanel>重新置放。 <xref:System.Windows.Forms.ToolStrip> `false` <xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ToolStripPanel>會忽略<xref:System.Windows.Forms.ToolStrip.Stretch%2A>屬性, 如果屬性為, 則的大小會隨著專案新增至而增加。 `Dock` 一般而言, <xref:System.Windows.Forms.ToolStrip>不會參與定位順序。

- 已停駐

  <xref:System.Windows.Forms.ToolStrip>會放在容器中固定位置的一端, 而且其大小會在其停駐的整個邊緣上展開。 一般而言, <xref:System.Windows.Forms.ToolStrip>不會參與定位順序。

- 絕對位置

  就像其他控制項一樣, 它是<xref:System.Windows.Forms.Control.Location%2A>由屬性所放置、具有固定的大小, 而且通常會參與定位順序。 <xref:System.Windows.Forms.ToolStrip>

#### <a name="keyboard-interaction"></a>鍵盤互動

##### <a name="access-keys"></a>存取金鑰

[存取金鑰] 結合或遵循 ALT 鍵, 是使用鍵盤來啟動控制項的一種方式。 <xref:System.Windows.Forms.ToolStrip>支援明確和隱含的存取金鑰。 明確定義會使用字母前面加上連字號 (&)。 隱含定義使用的演算法會根據指定`Text`屬性中的字元順序, 嘗試尋找相符的專案。

##### <a name="shortcut-keys"></a>快速鍵

所使用<xref:System.Windows.Forms.MenuStrip>的快速鍵會使用<xref:System.Windows.Forms.Keys>列舉的組合 (不是特定順序) 來定義快速鍵。 您也可以使用<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A>屬性來顯示只有文字的快速鍵, 例如顯示 "Del", 而不是 "delete"。

##### <a name="navigation"></a>巡覽

ALT 鍵會啟用所<xref:System.Windows.Forms.MenuStrip>指向<xref:System.Windows.Forms.Form.MainMenuStrip%2A>的。 在那裡, CTRL + TAB 會在<xref:System.Windows.Forms.ToolStrip> s 中`ToolStripPanel`的控制項之間流覽。 數位鍵臺上的 TAB 鍵和方向鍵會在中<xref:System.Windows.Forms.ToolStrip>的專案之間流覽。 特殊演算法會處理溢位區域中的導覽。 空格鍵會選取<xref:System.Windows.Forms.ToolStripButton>、 <xref:System.Windows.Forms.ToolStripDropDownButton>或<xref:System.Windows.Forms.ToolStripSplitButton>。

##### <a name="focus-and-validation"></a>焦點和驗證

由 ALT 鍵啟動時, <xref:System.Windows.Forms.MenuStrip>或通常不會從目前具有焦點的控制項中取得或<xref:System.Windows.Forms.ToolStrip>移除焦點。 如果在<xref:System.Windows.Forms.MenuStrip>或的下拉式<xref:System.Windows.Forms.MenuStrip>集中有控制項裝載, 則當使用者按下 TAB 鍵時, 控制項會取得焦點。 一般而言, <xref:System.Windows.Forms.Control.GotFocus>當鍵盤啟動<xref:System.Windows.Forms.Control.LostFocus>時<xref:System.Windows.Forms.Control.Enter>, 的<xref:System.Windows.Forms.Control.Leave> 、 <xref:System.Windows.Forms.MenuStrip> 、和事件可能不會引發。 在這種情況下, <xref:System.Windows.Forms.MenuStrip.MenuActivate>請<xref:System.Windows.Forms.MenuStrip.MenuDeactivate>改用和事件。

預設<xref:System.Windows.Forms.ToolStrip.CausesValidation%2A>為`false`。 在<xref:System.Windows.Forms.ContainerControl.Validate%2A>您的表單上明確呼叫以執行驗證。

#### <a name="layout"></a>配置

您可以<xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ToolStripLayoutStyle>使用<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>屬性來選擇的其中一個成員, 以控制版面配置。

##### <a name="stack-layouts"></a>堆疊版面配置

堆疊是在兩端並排<xref:System.Windows.Forms.ToolStrip>排列專案。 下列清單描述堆疊版面配置。

- <xref:System.Windows.Forms.ToolStripLayoutStyle.StackWithOverflow>是預設值。 這項設定會<xref:System.Windows.Forms.ToolStrip>讓根據<xref:System.Windows.Forms.ToolStrip.Orientation%2A>屬性自動改變其版面配置, 以處理拖放和停駐案例。

- <xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>以垂直<xref:System.Windows.Forms.ToolStrip>方式呈現彼此旁的專案。

- <xref:System.Windows.Forms.ToolStripLayoutStyle.HorizontalStackWithOverflow>以水準<xref:System.Windows.Forms.ToolStrip>方式呈現彼此連續的專案。

##### <a name="other-features-of-stack-layouts"></a>堆疊版面配置的其他功能

<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>決定專案對齊的<xref:System.Windows.Forms.ToolStrip>結尾。

當專案不符合<xref:System.Windows.Forms.ToolStrip>時, 就會自動顯示溢位按鈕。 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>屬性設定會決定專案是否會出現在溢位區域中 (如有需要), 或永遠不顯示。

在事件中, 您可以<xref:System.Windows.Forms.ToolStripItem.Placement%2A>檢查屬性, 以判斷專案是否放在主要<xref:System.Windows.Forms.ToolStrip>、溢<xref:System.Windows.Forms.ToolStrip>位, 或目前未顯示。 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> 專案不會顯示的一般原因是專案無法放在主要<xref:System.Windows.Forms.ToolStrip>的上, 而且其<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>屬性設定為<xref:System.Windows.Forms.ToolStripItemOverflow.Never>。

將它放<xref:System.Windows.Forms.ToolStripPanel>在並將其設定為, 即可<xref:System.Windows.Forms.ToolStrip.GripStyle%2A>將其設為<xref:System.Windows.Forms.ToolStripGripStyle.Visible>。 <xref:System.Windows.Forms.ToolStrip>

##### <a name="other-layout-options"></a>其他版面配置選項

其他版面配置選項為<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>和<xref:System.Windows.Forms.ToolStripLayoutStyle.Table>。

##### <a name="flow-layout"></a>流程配置

<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>layout 是<xref:System.Windows.Forms.ContextMenuStrip>、 <xref:System.Windows.Forms.ToolStripDropDownMenu>和<xref:System.Windows.Forms.ToolStripOverflow>的預設值。 其類似<xref:System.Windows.Forms.FlowLayoutPanel>于。 <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>版面配置的功能如下:

- 的所有功能<xref:System.Windows.Forms.FlowLayoutPanel>都是<xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>由屬性所公開。 您必須將<xref:System.Windows.Forms.LayoutSettings>類別轉換<xref:System.Windows.Forms.FlowLayoutSettings>成類別。

- 您可以使用程式<xref:System.Windows.Forms.ToolStripItem.Dock%2A>代碼<xref:System.Windows.Forms.ToolStripItem.Anchor%2A>中的和屬性, 以對齊資料列內的專案。

- 忽略 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> 屬性。

- 在此<xref:System.Windows.Forms.ToolStrip.LayoutCompleted>事件中, 您可以<xref:System.Windows.Forms.ToolStripItem.Placement%2A>檢查屬性, 以判斷專案是否放在主要<xref:System.Windows.Forms.ToolStrip>或不符合。

- 不會轉譯此底框, 因此<xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ToolStripPanel>無法移動<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>中版面配置樣式中的。

- [ <xref:System.Windows.Forms.ToolStrip>溢位] 按鈕不會轉譯<xref:System.Windows.Forms.ToolStripItem.Overflow%2A> , 而且會被忽略。

##### <a name="table-layout"></a>資料表版面配置

<xref:System.Windows.Forms.ToolStripLayoutStyle.Table>版面配置是的預設<xref:System.Windows.Forms.StatusStrip>值。 其類似<xref:System.Windows.Forms.TableLayoutPanel>于。 <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>版面配置的功能如下:

- 的所有功能<xref:System.Windows.Forms.TableLayoutPanel>都是<xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>由屬性所公開。 您必須將<xref:System.Windows.Forms.LayoutSettings>類別轉換<xref:System.Windows.Forms.TableLayoutSettings>成類別。

- 您可以使用程式<xref:System.Windows.Forms.ToolStripItem.Dock%2A>代碼<xref:System.Windows.Forms.ToolStripItem.Anchor%2A>中的和屬性, 對齊資料表單元格中的專案。

- 忽略 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> 屬性。

- 在此<xref:System.Windows.Forms.ToolStrip.LayoutCompleted>事件中, 您可以<xref:System.Windows.Forms.ToolStripItem.Placement%2A>檢查屬性, 以判斷專案是否放在主要<xref:System.Windows.Forms.ToolStrip>或不符合。

- 不會轉譯此底框, 因此<xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ToolStripPanel>無法移動<xref:System.Windows.Forms.ToolStripLayoutStyle.Table>中版面配置樣式中的。

- [ <xref:System.Windows.Forms.ToolStrip>溢位] 按鈕不會轉譯<xref:System.Windows.Forms.ToolStripItem.Overflow%2A> , 而且會被忽略。

## <a name="toolstripitem"></a>ToolStripItem

下列主題描述<xref:System.Windows.Forms.ToolStripItem>和衍生自它的控制項。

<xref:System.Windows.Forms.ToolStripItem>是進入的<xref:System.Windows.Forms.ToolStrip>所有專案的抽象基類。 下列物件模型會顯示<xref:System.Windows.Forms.ToolStripItem>繼承階層架構。

![顯示 ToolStripItem 物件模型的圖表。](./media/toolstrip-control-architecture/toolstripitem-object-model.gif)

<xref:System.Windows.Forms.ToolStripItem>類別會直接繼承自<xref:System.Windows.Forms.ToolStripItem>, 或透過<xref:System.Windows.Forms.ToolStripControlHost>或<xref:System.Windows.Forms.ToolStripDropDownItem>間接繼承<xref:System.Windows.Forms.ToolStripItem>自。

<xref:System.Windows.Forms.ToolStripItem>控制項必須<xref:System.Windows.Forms.ToolStrip>包含在、、 <xref:System.Windows.Forms.StatusStrip>或<xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip>中, 而且無法直接新增至表單。 各種容器類別的設計, 是為了包含適當的<xref:System.Windows.Forms.ToolStripItem>控制項子集。

下表列出<xref:System.Windows.Forms.ToolStripItem>內建控制項和其外觀最佳的容器。 雖然任何<xref:System.Windows.Forms.ToolStrip>專案都可以裝載于任何<xref:System.Windows.Forms.ToolStrip>衍生的容器中, 但這些專案已設計成可在下列容器中發揮最佳效果:

> [!NOTE]
> <xref:System.Windows.Forms.ToolStripDropDown>不會出現在設計工具的 [工具箱] 中。

|包含的專案|ToolStrip|MenuStrip|ContextMenuStrip|StatusStrip|ToolStripDropDown|
|--------------------|---------------|---------------|----------------------|-----------------|-----------------------|
|<xref:System.Windows.Forms.ToolStripButton>|是|否|否|否|是|
|<xref:System.Windows.Forms.ToolStripComboBox>|是|是|是|否|是|
|<xref:System.Windows.Forms.ToolStripSplitButton>|是|否|否|是|是|
|<xref:System.Windows.Forms.ToolStripLabel>|是|否|否|是|是|
|<xref:System.Windows.Forms.ToolStripSeparator>|是|是|是|否|是|
|<xref:System.Windows.Forms.ToolStripDropDownButton>|是|否|否|是|是|
|<xref:System.Windows.Forms.ToolStripTextBox>|是|是|是|否|[是]|
|<xref:System.Windows.Forms.ToolStripMenuItem>|否|是|是|否|否|
|<xref:System.Windows.Forms.ToolStripStatusLabel>|否|否|否|[是]|否|
|<xref:System.Windows.Forms.ToolStripProgressBar>|[是]|否|否|[是]|否|
|<xref:System.Windows.Forms.ToolStripControlHost>|是|是|否|是|是|

### <a name="toolstripbutton"></a>ToolStripButton

<xref:System.Windows.Forms.ToolStripButton>是的按鈕專案<xref:System.Windows.Forms.ToolStrip>。 您可以使用各種框線樣式來顯示它, 也可以用它來表示和啟動操作狀態。 您也可以將它定義為預設具有焦點。

### <a name="toolstriplabel"></a>ToolStripLabel

會在控制項中<xref:System.Windows.Forms.ToolStrip> 提供標籤功能。<xref:System.Windows.Forms.ToolStripLabel> <xref:System.Windows.Forms.ToolStripLabel> 類似于預設不會取得焦點,而且不會呈現為推送或<xref:System.Windows.Forms.ToolStripButton>反白顯示的。

<xref:System.Windows.Forms.ToolStripLabel>因為裝載的專案支援存取金鑰。

使用<xref:System.Windows.Forms.LinkLabel.LinkColor%2A> <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>上的、<xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>和屬性,以支援中的連結控制項。<xref:System.Windows.Forms.ToolStripLabel> <xref:System.Windows.Forms.ToolStrip>

### <a name="toolstripstatuslabel"></a>ToolStripStatusLabel

<xref:System.Windows.Forms.ToolStripStatusLabel>是專為在<xref:System.Windows.Forms.ToolStripLabel>中<xref:System.Windows.Forms.StatusStrip>使用而設計的版本。 這些特殊功能包括<xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>、 <xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A>和<xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>。

### <a name="toolstripseparator"></a>ToolStripSeparator

會<xref:System.Windows.Forms.ToolStripSeparator>將垂直或水平線加入工具列或功能表, 視方向而定。 它會提供專案的群組或區別, 例如功能表上的專案。

您可以從下拉式<xref:System.Windows.Forms.ToolStripSeparator>清單中選擇, 在設計階段加入。 不過, 您也可以在設計工具<xref:System.Windows.Forms.ToolStripSeparator>範本節點或<xref:System.Windows.Forms.ToolStripItemCollection.Add%2A>方法中輸入連字號 (-), 以自動建立。

### <a name="toolstripcontrolhost"></a>ToolStripControlHost

<xref:System.Windows.Forms.ToolStripControlHost>是<xref:System.Windows.Forms.ToolStripComboBox>、 <xref:System.Windows.Forms.ToolStripTextBox>和的抽象基類。<xref:System.Windows.Forms.ToolStripProgressBar> <xref:System.Windows.Forms.ToolStripControlHost>可以透過兩種方式裝載其他控制項, 包括自訂控制項:

- 使用衍生自<xref:System.Windows.Forms.Control>的類別來建立。 <xref:System.Windows.Forms.ToolStripControlHost> 若要完整存取裝載的控制項和屬性, 您必須將<xref:System.Windows.Forms.ToolStripControlHost.Control%2A>屬性轉換回它所代表的實體類別。

- 延伸<xref:System.Windows.Forms.ToolStripControlHost>, 並在繼承類別的無參數函式中, 呼叫基類的函式, 以傳遞衍生<xref:System.Windows.Forms.Control>自的類別。 此選項可讓您包裝通用控制項方法和屬性, 以便在中<xref:System.Windows.Forms.ToolStrip>輕鬆存取。

### <a name="toolstripcombobox"></a>ToolStripComboBox

<xref:System.Windows.Forms.ToolStripComboBox>是針對<xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.ToolStrip>在中裝載而優化的。 裝載控制項的屬性和事件的子集會在<xref:System.Windows.Forms.ToolStripComboBox>層級公開, 但基礎<xref:System.Windows.Forms.ComboBox>控制項可透過<xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A>屬性進行完整存取。

### <a name="toolstriptextbox"></a>ToolStripTextBox

<xref:System.Windows.Forms.ToolStripTextBox>是針對<xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.ToolStrip>在中裝載而優化的。 裝載控制項的屬性和事件的子集會在<xref:System.Windows.Forms.ToolStripTextBox>層級公開, 但基礎<xref:System.Windows.Forms.TextBox>控制項可透過<xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A>屬性進行完整存取。

### <a name="toolstripprogressbar"></a>ToolStripProgressBar

<xref:System.Windows.Forms.ToolStripProgressBar>是針對<xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ToolStrip>在中裝載而優化的。 裝載控制項的屬性和事件的子集會在<xref:System.Windows.Forms.ToolStripProgressBar>層級公開, 但基礎<xref:System.Windows.Forms.ProgressBar>控制項可透過<xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A>屬性進行完整存取。

### <a name="toolstripdropdownitem"></a>ToolStripDropDownItem

<xref:System.Windows.Forms.ToolStripDropDownItem>是<xref:System.Windows.Forms.ToolStripMenuItem>、 <xref:System.Windows.Forms.ToolStripDropDownButton>和的抽象基類,可以直接裝載專案,或在下拉式容器中裝載其他專案。<xref:System.Windows.Forms.ToolStripSplitButton> 若要這麼做, 您<xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A>可以將屬性設定為<xref:System.Windows.Forms.ToolStrip.Items%2A>,並 <xref:System.Windows.Forms.ToolStripDropDown>設定的屬性。 <xref:System.Windows.Forms.ToolStripDropDown> 直接透過<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A>屬性存取這些下拉式專案。

### <a name="toolstripmenuitem"></a>ToolStripMenuItem

<xref:System.Windows.Forms.ToolStripMenuItem>是, 可與和<xref:System.Windows.Forms.ToolStripDropDownMenu>搭配<xref:System.Windows.Forms.ContextMenuStrip>使用, 以處理功能表的特殊醒目提示、版面配置和資料行相片順序。 <xref:System.Windows.Forms.ToolStripDropDownItem>

### <a name="toolstripdropdownbutton"></a>ToolStripDropDownButton

<xref:System.Windows.Forms.ToolStripDropDownButton>看起來<xref:System.Windows.Forms.ToolStripButton>像, 但它會在使用者按一下時顯示下拉式區域。 藉由設定<xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A>屬性來隱藏或顯示下拉箭號。 <xref:System.Windows.Forms.ToolStripDropDownButton>裝載, <xref:System.Windows.Forms.ToolStripOverflowButton>其會顯示溢位的<xref:System.Windows.Forms.ToolStrip>專案。

### <a name="toolstripsplitbutton"></a>ToolStripSplitButton

<xref:System.Windows.Forms.ToolStripSplitButton>結合按鈕和下拉按鈕功能。

使用屬性, 即可將所<xref:System.Windows.Forms.Control.Click>選下拉式專案的事件與按鈕上顯示的專案進行同步處理。 <xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A>

### <a name="toolstripitem-generic-features"></a>ToolStripItem 一般功能

<xref:System.Windows.Forms.ToolStripItem>提供下列一般功能和繼承控制項的選項:

- 核心事件

- 影像處理

- 對齊

- 文字和影像關聯性

- 顯示樣式

#### <a name="core-events"></a>核心事件

<xref:System.Windows.Forms.ToolStripItem>控制項會接收自己的點擊、滑鼠和繪製事件, 也可以執行一些鍵盤前置處理。

#### <a name="image-handling"></a>影像處理

<xref:System.Windows.Forms.ToolStripItem.Image%2A>、 、、<xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A>和屬性<xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A>與影像處理的各個層面有關。 <xref:System.Windows.Forms.ToolStripItem.ImageKey%2A> <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> 直接設定這些<xref:System.Windows.Forms.ToolStrip>屬性, 或設定 [僅限<xref:System.Windows.Forms.ToolStrip.ImageList%2A>執行時間] 屬性, 即可使用控制項中的影像。

影像縮放是由<xref:System.Windows.Forms.ToolStrip>和<xref:System.Windows.Forms.ToolStripItem>中的屬性互動所決定, 如下所示:

- <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A>這是由影像<xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A>設定和<xref:System.Windows.Forms.ToolStrip.AutoSize%2A>容器設定的組合所決定的最終影像尺規。

  - 如果<xref:System.Windows.Forms.ToolStrip.AutoSize%2A> <xref:System.Windows.Forms.ToolStripItemImageScaling>為`true` (預設值) 且為<xref:System.Windows.Forms.ToolStripItemImageScaling.SizeToFit>, 則不會進行任何影像縮放<xref:System.Windows.Forms.ToolStrip> , 而且大小會是最大專案的大小, 或指定的最小大小。

  - 如果<xref:System.Windows.Forms.ToolStrip.AutoSize%2A>是`false` ,且<xref:System.Windows.Forms.ToolStripItemImageScaling>為, 則<xref:System.Windows.Forms.ToolStripItemImageScaling.None>不<xref:System.Windows.Forms.ToolStrip>會發生影像或縮放。

#### <a name="alignment"></a>對齊

<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>屬性的值會決定專案出現的<xref:System.Windows.Forms.ToolStrip>結尾。 只有<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>當的版面配置樣式<xref:System.Windows.Forms.ToolStrip>設定為其中一個堆疊溢位值時, 屬性才有效。

專案會依照專案出現<xref:System.Windows.Forms.ToolStrip>在 items 集合中的順序, 放在上。 若要以程式設計方式變更專案的配置位置, <xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A>請使用方法來移動集合中的專案。 這個方法會移動專案, 但不會將它複製。

#### <a name="text-and-image-relationship"></a>文字和影像關聯性

屬性會根據上的文字, 定義影像的相對位置。 <xref:System.Windows.Forms.ToolStripItem> <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> 缺少影像、文字或兩者的專案會被視為特殊情況, 因此<xref:System.Windows.Forms.ToolStripItem>不會針對遺漏的元素或元素顯示空白位置。

#### <a name="display-style"></a>顯示樣式

<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>可讓您設定專案的文字和影像屬性值, 同時只顯示您想要的內容。 這通常用來在不同的內容中顯示相同的專案時, 只變更顯示樣式。

## <a name="accessory-classes"></a>裝飾類別

提供各種其他功能的類別包括:

- <xref:System.Windows.Forms.ToolStripManager>支援<xref:System.Windows.Forms.ToolStrip>整個應用程式的相關工作, 例如合併、設定和轉譯器選項。

- <xref:System.Windows.Forms.ToolStripRenderer>可讓您<xref:System.Windows.Forms.ToolStrip>輕鬆地將特定樣式或主題套用至。

- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>根據可替換的色彩表 (<xref:System.Windows.Forms.ProfessionalColorTable>) 建立畫筆和筆刷。

- <xref:System.Windows.Forms.ToolStripSystemRenderer>將系統色彩和平面視覺化樣式套用至<xref:System.Windows.Forms.ToolStrip>應用程式。

- <xref:System.Windows.Forms.ToolStripContainer>類似<xref:System.Windows.Forms.SplitContainer>于。 它會使用四個固定的側邊<xref:System.Windows.Forms.ToolStripPanel>面板 (的實例) 和一個中央面板<xref:System.Windows.Forms.ToolStripContentPanel>(的實例) 來建立一般的相片順序。 您不能移除側邊面板, 但是可以隱藏它們。 您不能移除或隱藏中央面板。 您可以在側邊面板<xref:System.Windows.Forms.ToolStrip>中<xref:System.Windows.Forms.MenuStrip>排列一<xref:System.Windows.Forms.StatusStrip>或多個、或控制項, 也可以使用中央面板來進行其他控制項。 <xref:System.Windows.Forms.ToolStripContentPanel>也提供一種方式, 可讓您取得表單主體的轉譯器支援, 以提供一致的外觀。 <xref:System.Windows.Forms.ToolStripContainer>不支援多個檔介面 (MDI)。

- <xref:System.Windows.Forms.ToolStripPanel>提供移動和排列<xref:System.Windows.Forms.ToolStrip>控制項的空間。 如果您選擇, 您可以只使用一個面板, 並且<xref:System.Windows.Forms.ToolStripPanel>在 MDI 案例中運作良好。

## <a name="see-also"></a>另請參閱

- [ToolStrip 控制項概觀](toolstrip-control-overview-windows-forms.md)
- [ToolStrip 技術摘要](toolstrip-technology-summary.md)
- [ToolStrip 控制項](toolstrip-control-windows-forms.md)
- [MenuStrip 控制項](menustrip-control-windows-forms.md)
- [StatusStrip 控制項](statusstrip-control.md)
- [ContextMenuStrip 控制項](contextmenustrip-control.md)
- [BindingNavigator 控制項](bindingnavigator-control-windows-forms.md)
