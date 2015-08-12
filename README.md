'Programmed by: Joshua Boeckholt
'Screen resolution: 1280 X 1024
'Approximate number of hours worked: 4.5
'Purpose: To calculate income tax based on different incomes entered and submitted into a text box.


Public Class TaxCalc

    Dim TAX As Decimal = "0" 'Will use TAX as my print variable and it will hold the equation

    Private Sub AddBtn_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles AddBtn.Click

        'making TAX equal to the tax formula equation I came up with based on the value of the IncomeTxtBox input.
        If IncomeTxtBox.Text = "" Then
            MsgBox("! PLEASE ENTER A VALUE !")
        ElseIf IncomeTxtBox.Text <= 8025 Then
            TAX = IncomeTxtBox.Text * 0.1
        ElseIf IncomeTxtBox.Text > 8025 And IncomeTxtBox.Text < 32550 Then
            TAX = (IncomeTxtBox.Text - 8025) * 0.15 + 802.5
        ElseIf IncomeTxtBox.Text > 32550 And IncomeTxtBox.Text < 78850 Then
            TAX = (IncomeTxtBox.Text - 32550) * 0.25 + 4481.25
        ElseIf IncomeTxtBox.Text > 78850 And IncomeTxtBox.Text < 164550 Then
            TAX = (IncomeTxtBox.Text - 78850) * 0.28 + 16056.25
        ElseIf IncomeTxtBox.Text > 164550 And IncomeTxtBox.Text < 357700 Then
            TAX = (IncomeTxtBox.Text - 164550) * 0.33 + 40052.25
        ElseIf IncomeTxtBox.Text > 357700 Then
            TAX = (IncomeTxtBox.Text - 357700) * 0.35 + 103791.75
        End If

        IncomeTxtBox.Text = FormatCurrency(IncomeTxtBox.Text)
        TAX = FormatCurrency(TAX)

        'If nothing was entered in the box, do nothing (besides popping up the msg box in the previous IF statement. Else, proceed to make the calculations and print the income entered and tax.
        If IncomeTxtBox.Text = "" Then
            'left blank so nothing is added to the List Box if nothing is put into the Text Box.
        Else
            ResultListBox.Items.Add("INCOME: " & IncomeTxtBox.Text & "   TAX: " & TAX)
            IncomeTxtBox.Clear() 'clears the List box automatically after button press incase user wants to put more values.
        End If


    End Sub

    Private Sub ClearBtn_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles ClearBtn.Click
        ResultListBox.Items.Clear()  'clears the list box.
    End Sub

    Private Sub ExitBtn_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles ExitBtn.Click
        Close() 'Closes the program.
    End Sub

    Private Sub Timer1_Tick(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Timer1.Tick
        timeLBL.Text = TimeOfDay.ToLongTimeString()  'gets the time and sets the time lbl as system time. Used for a clock.
    End Sub

End Class
