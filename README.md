# blok
database
Public Class Form1

    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        'TODO: This line of code loads data into the 'Blok6DataSet.numberDog' table. You can move, or remove it, as needed.
        Me.NumberDogTableAdapter.Fill(Me.Blok6DataSet.numberDog)
        'TODO: This line of code loads data into the 'Blok6DataSet.numberPers' table. You can move, or remove it, as needed.
        Me.NumberPersTableAdapter.Fill(Me.Blok6DataSet.numberPers)
        'TODO: This line of code loads data into the 'Blok6DataSet.Addresses' table. You can move, or remove it, as needed.
        Me.AddressesTableAdapter.Fill(Me.Blok6DataSet.Addresses)
        'TODO: This line of code loads data into the 'Blok6DataSet.january' table. You can move, or remove it, as needed.
        Me.JanuaryTableAdapter.Fill(Me.Blok6DataSet.january)

    End Sub

   
    Private Sub BtnAddNew_Click(sender As Object, e As EventArgs) Handles BtnAddNew.Click
        On Error GoTo AddNewErr
        JanuaryBindingSource.AddNew()
ErrExe:
        Exit Sub
AddNewErr:
        MsgBox("Добавете номер на апартамент!")
        Resume ErrExe
    End Sub

    Private Sub BtnSave_Click(sender As Object, e As EventArgs) Handles BtnSave.Click
        On Error GoTo SaveErr
        JanuaryBindingSource.EndEdit()
        JanuaryTableAdapter.Update(Blok6DataSet.january)
ErrExe:
        Exit Sub
SaveErr:
        MsgBox("Повтарящ се или грешен номер на апартамент!")
        JanuaryBindingSource.CancelEdit()
        Resume ErrExe
    End Sub

    Private Sub DataGridView1_CellContentClick(sender As Object, e As DataGridViewCellEventArgs) Handles DataGridView1.CellContentClick

    End Sub

    Private Sub BtnPrev_Click(sender As Object, e As EventArgs) Handles BtnPrev.Click
        On Error GoTo NextError
        JanuaryBindingSource.MoveNext()

ErrExe:
        Exit Sub
NextError:
        MsgBox("Не сте въвели номер на апартамент!", MsgBoxStyle.Critical, _
               "Въведете друг.")
        Resume ErrExe
    End Sub

    Private Sub BtnClose_Click(sender As Object, e As EventArgs) Handles BtnClose.Click
        Dim msg As String = "Желаете ли да излезете?"
        Dim title As String = "Изход от приложението"
        If MessageBox.Show(msg, title, MessageBoxButtons.YesNo, _
                          MessageBoxIcon.Question, MessageBoxDefaultButton.Button1) = _
                       Windows.Forms.DialogResult.Yes Then
            Me.Close()
        End If
    End Sub

    Private Sub BtnUndo_Click(sender As Object, e As EventArgs) Handles BtnUndo.Click
        JanuaryBindingSource.CancelEdit()
    End Sub

    Private Sub ComboBox1_SelectedIndexChanged(sender As Object, e As EventArgs) Handles ComboBox1.SelectedIndexChanged

    End Sub

    Private Sub BtnBack_Click(sender As Object, e As EventArgs) Handles BtnBack.Click
        JanuaryBindingSource.MovePrevious()
    End Sub
End Class
