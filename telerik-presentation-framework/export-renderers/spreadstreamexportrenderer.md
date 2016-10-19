---
title: SpreadStreamExportRenderer
page_title: SpreadStreamExportRenderer | Telerik Presentation Framework
description: SpreadStreamExportRenderer
slug: winforms/telerik-presentation-framework/export-renderers/spreadstreamexportrenderer
tags: spreadexportrenderer
published: True
position: 2
---

# SpreadStreamExportRenderer

This class exposes methods and events needed to export using the [SpreadStreamExport]({%slug winforms/gridview/exporting-data/stream-export}).


## Events

### WorksheetCreated 

Occurs when a new worksheet is created.It is suitable to set the columns width or rows at the document begging or insert cells before the firs column.

#### Adding a Header Row.
 
{{source=..\SamplesCS\GridView\ExportingData\SpreadStreamExportCode.cs region=WorksheetCreated}} 
{{source=..\SamplesVB\GridView\ExportingData\SpreadStreamExportCode.vb region=WorksheetCreated}}
````C#
private void Renderer_WorksheetCreated(object sender, SpreadStreamWorksheetEventArgs e)
{
    SpreadStreamExportRenderer exportRenderer = sender as SpreadStreamExportRenderer;
    exportRenderer.CreateRow();
    exportRenderer.SetRowHeight(50, true);
    for (int i = 0; i < this.radGridView1.Columns.Count; i++)
    {
        SpreadCellFormat format = new SpreadCellFormat()
        {
            Fill = SpreadPatternFill.CreateSolidFill(new SpreadColor(200, 200, 200))
        };
        exportRenderer.CreateCell();
        exportRenderer.ApplyCellFormat(format);
        if (this.radGridView1.Columns.Count / 2 == i)
        {
            exportRenderer.SetCellValue("This is HEADER row.");
        }
    }
}

````
````VB.NET
Private Sub Renderer_WorksheetCreated(ByVal sender As Object, ByVal e As SpreadStreamWorksheetEventArgs)
    Dim exportRenderer As SpreadStreamExportRenderer = TryCast(sender, SpreadStreamExportRenderer)
    exportRenderer.CreateRow()
    exportRenderer.SetRowHeight(50, True)
    For i As Integer = 0 To Me.radGridView1.Columns.Count - 1
        Dim format As New SpreadCellFormat() With {.Fill = SpreadPatternFill.CreateSolidFill(New SpreadColor(200, 200, 200))}
        exportRenderer.CreateCell()
        exportRenderer.ApplyCellFormat(format)
        If Me.radGridView1.Columns.Count \ 2 = i Then
            exportRenderer.SetCellValue("This is HEADER row.")
        End If
    Next i
End Sub

````



{{endregion}} 

### WorksheetExporting

Occurs when a worksheet is about to be exported. This is suitable place to add rows at the end of the document.

#### Adding a Footer row.

{{source=..\SamplesCS\GridView\ExportingData\SpreadStreamExportCode.cs region=WorksheetExporting}} 
{{source=..\SamplesVB\GridView\ExportingData\SpreadStreamExportCode.vb region=WorksheetExporting}}
````C#
private void Renderer_WorksheetExporting(object sender, SpreadStreamWorksheetEventArgs e)
{
    SpreadStreamExportRenderer exportRenderer = sender as SpreadStreamExportRenderer;
    exportRenderer.CreateRow();
    exportRenderer.SetRowHeight(50, true);
    for (int i = 0; i < this.radGridView1.Columns.Count; i++)
    {
        SpreadCellFormat format = new SpreadCellFormat()
        {
            Fill = SpreadPatternFill.CreateSolidFill(new SpreadColor(200, 200, 200))
        };
        exportRenderer.CreateCell();
        exportRenderer.ApplyCellFormat(format);
        if (this.radGridView1.Columns.Count / 2 == i)
        {
            exportRenderer.SetCellValue("This is FOOTER row.");
        }
    }
}

````
````VB.NET
Private Sub Renderer_WorksheetExporting(ByVal sender As Object, ByVal e As SpreadStreamWorksheetEventArgs)
    Dim exportRenderer As SpreadStreamExportRenderer = TryCast(sender, SpreadStreamExportRenderer)
    exportRenderer.CreateRow()
    exportRenderer.SetRowHeight(50, True)
    For i As Integer = 0 To Me.radGridView1.Columns.Count - 1
        Dim format As New SpreadCellFormat() With {.Fill = SpreadPatternFill.CreateSolidFill(New SpreadColor(200, 200, 200))}
        exportRenderer.CreateCell()
        exportRenderer.ApplyCellFormat(format)
        If Me.radGridView1.Columns.Count \ 2 = i Then
            exportRenderer.SetCellValue("This is FOOTER row.")
        End If
    Next i
End Sub

````



{{endregion}} 

### WorkbookCreated

This is suitable place to add and/or modify Excel cell styles. Detailed information is available here: [CellStyles](http://docs.telerik.com/devtools/document-processing/libraries/radspreadstreamprocessing/features/cell-styles)