---
title: 將屬性公開至 [屬性] 視窗 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7853b956e88ac1b239792ad96fb094c1a7c0a3c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490524"
---
# <a name="exposing-properties-to-the-properties-window"></a>將屬性公開至屬性視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[公開的屬性，以 [屬性] 視窗](https://docs.microsoft.com/visualstudio/extensibility/exposing-properties-to-the-properties-window)。  
  
本逐步解說會公開物件的公用屬性**屬性**視窗。 您對這些屬性的變更會反映在**屬性**視窗。  
  
## <a name="prerequisites"></a>必要條件  
 從 Visual Studio 2015 中，從下載中心取得未安裝 Visual Studio SDK。 包含為 Visual Studio 安裝程式的選用功能。 您也可以在稍後安裝 VS SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
## <a name="exposing-properties-to-the-properties-window"></a>將屬性公開至屬性視窗  
 在本節中，方法，您可以建立自訂工具視窗，並顯示相關聯的視窗窗格物件中的公用屬性**屬性**視窗。  
  
#### <a name="to-expose-properties-to-the-properties-window"></a>若要公開屬性，以 [屬性] 視窗  
  
1.  每個 Visual Studio 擴充功能開始 VSIX 部署專案，以將包含的延伸模組資產。 建立[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]VSIX 專案，名為`MyObjectPropertiesExtension`。 您可以找到在 VSIX 專案範本**新的專案**下方的對話方塊**Visual C# / 擴充性**。  
  
2.  藉由新增名為的自訂工具視窗項目範本加入工具視窗`MyToolWindow`。 在 **方案總管**，以滑鼠右鍵按一下專案節點，然後選取**新增 / 新項目**。 在 [**加入新項目] 對話方塊**，請移至**Visual C# 項目 / 擴充性**，然後選取**自訂工具視窗**。 在 **名稱**底部的對話方塊欄位中，將檔案名稱變更為`MyToolWindow.cs`。 如需如何建立自訂工具視窗的詳細資訊，請參閱[工具視窗建立擴充](../extensibility/creating-an-extension-with-a-tool-window.md)。  
  
3.  開啟 MyToolWindow.cs 並新增下列 using 陳述式：  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4.  現在加入以下欄位，供`MyToolWindow`類別。  
  
    ```csharp  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5.  將下列程式碼新增至 MyToolWindow 類別。  
  
    ```csharp  
    private ITrackSelection TrackSelection  
    {  
        get  
        {  
            if (trackSel == null)  
                trackSel =  
                   GetService(typeof(STrackSelection)) as ITrackSelection;  
            return trackSel;  
        }  
    }  
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     `TrackSelection`屬性使用`GetService`若要取得`STrackSelection`服務，提供<xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>介面。 `OnToolWindowCreated`事件處理常式和`SelectList`方法一起建立一份所選物件包含只有工具視窗窗格中的物件本身。 `UpdateSelection`方法會告訴**屬性**視窗，以顯示工具視窗窗格的公用屬性。  
  
6.  建置此專案並開始偵錯。 Visual Studio 的實驗執行個體應該會出現。  
  
7.  如果**屬性**看不到視窗，請按 F4 開啟。  
  
8.  開啟**MyToolWindow**視窗。 您可以找到它**檢視 / 其他 Windows**。  
  
     視窗隨即開啟，而且 [視窗] 窗格的公用屬性會出現在**屬性**視窗。  
  
9. 變更**Caption**中的屬性**屬性**視窗**My 的物件屬性**。  
  
     MyToolWindow 視窗的標題會隨之改變。  
  
## <a name="exposing-tool-window-properties"></a>公開的工具視窗屬性  
 在本節中，您可以加入工具視窗，並公開其屬性。 您對內容的變更會反映在**屬性**視窗。  
  
#### <a name="to-expose-tool-window-properties"></a>若要公開 （expose） 工具視窗屬性  
  
1.  開啟 MyToolWindow.cs，並加入公用的布林值屬性 IsChecked MyToolWindow 類別。  
  
    ```csharp  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;   
        }  
        set {  
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;  
        }  
    }  
    ```  
  
     這個屬性會取得其狀態，從您將在稍後建立的 WPF 核取方塊。  
  
2.  開啟 MyToolWindowControl.xaml.cs，並以下列程式碼取代 MyToolWindowControl 建構函式。  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     這可讓`MyToolWindowControl`存取`MyToolWindow`窗格。  
  
3.  在 MyToolWindow.cs，變更`MyToolWindow`建構函式，如下所示：  
  
    ```csharp  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  變更 MyToolWindowControl [設計] 檢視。  
  
5.  [刪除] 按鈕，並將新增核取方塊，從**工具箱**至左上角。  
  
6.  加入 Checked 與 Unchecked 事件。 在 [設計] 檢視中選取此核取方塊。 中**屬性** 視窗中，按一下事件處理常式按鈕 (右上方的**屬性**視窗)。 尋找**核取**和型別**checkbox_Checked**文字方塊中，然後尋找**未核取**並輸入**checkbox_Unchecked**在文字方塊中。  
  
7.  將新增核取方塊事件處理常式：  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = true;  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.UpdateSelection();  
    }  
    ```  
  
8.  建置此專案並開始偵錯。  
  
9. 在實驗執行個體中，開啟**MyToolWindow**視窗。  
  
     視窗的內容中尋找**屬性**視窗。 **IsChecked**屬性會出現在視窗的底部底下**我的內容**類別目錄。  
  
10. 簽入的核取方塊**MyToolWindow**視窗。 **IsChecked**中**屬性** 視窗變更為**True**。 清除核取方塊，在**MyToolWindow**視窗。 **IsChecked**中**屬性** 視窗變更為**False**。 值變更**IsChecked**中**屬性**視窗。 中的核取方塊**MyToolWindow**視窗會變更，以符合新的值。  
  
    > [!NOTE]
    >  如果您必須處置的物件，會顯示在**屬性**視窗中，呼叫`OnSelectChange`使用`null`選取容器第一次。 之後處置物件的屬性，您可以變更為 已更新的選取項目容器<xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A>和<xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A>列出。  
  
## <a name="changing-selection-lists"></a>變更選取項目清單  
 在本節中，您要新增的基本屬性類別的選取項目清單，並使用工具視窗介面來選擇要顯示的選取項目清單。  
  
#### <a name="to-change-selection-lists"></a>若要變更選取項目清單  
  
1.  開啟 MyToolWindow.cs 並新增名為公用類別`Simple`。  
  
    ```csharp  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
        {  
            get { return someText; }  
            set { someText = value; }  
        }  
  
        [Category("My Properties")]  
        [Description("Read-only property")]  
        public bool ReadOnly  
        {  
            get { return false; }  
        }  
    }  
    ```  
  
2.  將 SimpleObject 屬性新增至 MyToolWindow 類別，再加上兩種方法可以切換**屬性** 視窗選取範圍視窗窗格之間和`Simple`物件。  
  
    ```csharp  
    private Simple simpleObject = null;  
    public Simple SimpleObject  
    {  
        get  
        {  
            if (simpleObject == null) simpleObject = new Simple();  
            return simpleObject;  
        }  
    }  
  
    public void SelectSimpleList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(SimpleObject);  
        SelectList(listObjects);  
    }  
  
    public void SelectThisList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
3.  在 MyToolWindowControl.cs，取代這些幾行程式碼中的核取方塊處理常式：  
  
    ```csharp  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
     {  
        pane.IsChecked = true;  
        pane.SelectSimpleList();  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.SelectThisList();  
        pane.UpdateSelection();  
    }  
    ```  
  
4.  建置此專案並開始偵錯。  
  
5.  在實驗執行個體中，開啟**MyToolWindow**視窗。  
  
6.  選取核取方塊，在**MyToolWindow**視窗。 **屬性** 視窗會顯示`Simple`物件屬性， **SomeText**並**ReadOnly**。 清除核取方塊。 視窗的公用屬性會出現在**屬性**視窗。  
  
    > [!NOTE]
    >  顯示名稱**SomeText**是**我文字**。  
  
## <a name="best-practice"></a>最佳作法  
 在本逐步解說，<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>實作，以便可選取的物件集合和所選的物件的集合相同的集合。 選取的物件會出現在屬性瀏覽器清單。 如需更完整的 ISelectionContainer 實作中，請參閱 Reference.ToolWindow 範例。  
  
 Visual Studio 工作階段之間保存的 visual Studio 工具視窗。 如需有關如何保存工具視窗狀態的詳細資訊，請參閱<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>。  
  
## <a name="see-also"></a>另請參閱  
 [擴充屬性和屬性視窗](../extensibility/extending-properties-and-the-property-window.md)
