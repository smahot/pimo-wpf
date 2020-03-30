+++
title = "Création dynamique de classe - Exercices"
weight = 302
pre = "<b>3.2 </b>"
+++

## 3.2 Création dynamique de classe <!-- omit in toc -->

- [Exercice 1 : Hello !](#exercice-1--hello)
- [Exercice 2 : La Checkbox](#exercice-2--la-checkbox)
- [Exercice 3 : Le Stack Panel](#exercice-3--le-stack-panel)
- [Exercice 4 : Le Canvas](#exercice-4--le-canvas)


### Exercice 1 : Hello !

{{% exercice %}}
Reproduisez à l’aide des boutons, d’un Canvas et d’une TextBox le résultat suivant de façon dynamique :
{{% /exercice %}}

![image1](/img/3.2/img01.png?height=300px)

{{% expand "Correction" %}}

```csharp
Canvas cv = new Canvas();
TextBox txtb = new TextBox();

Button h = new Button();
Button e = new Button();
Button l = new Button();
Button o = new Button();

Button excl = new Button();
Button esp = new Button();

public MainWindow()
{
    InitializeComponent();
    MakingGrid();
}

private void MakingGrid()
{
    cv.Height = 480;
    cv.Width = 420;
    txtb.IsEnabled = false;
    txtb.Height = 300;
    txtb.Width = 390;
    txtb.FontSize = 30;
    Canvas.SetLeft(txtb, 10);
    Canvas.SetTop(txtb, 10);
    cv.Children.Add(txtb);
    h.Height = 30;
    h.Width = 30;
    h.Content = "H";
    h.FontSize = 20;
    h.FontWeight = FontWeights.Bold;
    h.Background = Brushes.Honeydew;
    Canvas.SetLeft(h, 10);
    Canvas.SetTop(h, 320);
    h.Click += btn_h;
    cv.Children.Add(h);
    e.Height = 30;
    e.Width = 30;
    e.Content = "E";
    e.FontSize = 20;
    e.FontWeight = FontWeights.Bold;
    e.Background = Brushes.Honeydew;
    Canvas.SetLeft(e, 45);
    Canvas.SetTop(e, 320);
    e.Click += btn_e;
    cv.Children.Add(e);
    l.Height = 30;
    l.Width = 30;
    l.Content = "L";
    l.FontSize = 20;
    l.FontWeight = FontWeights.Bold;
    l.Background = Brushes.Honeydew;
    Canvas.SetLeft(l, 80);
    Canvas.SetTop(l, 320);
    l.Click += btn_l;
    cv.Children.Add(l);
    o.Height = 30;
    o.Width = 30;
    o.Content = "O";
    o.FontSize = 20;
    o.FontWeight = FontWeights.Bold;
    o.Background = Brushes.Honeydew;
    Canvas.SetLeft(o, 115);
    Canvas.SetTop(o, 320);
    o.Click += btn_o;
    cv.Children.Add(o);
    excl.Height = 30;
    excl.Width = 30;
    excl.Content = "!";
    excl.FontSize = 20;
    excl.FontWeight = FontWeights.Bold;
    excl.Background = Brushes.Honeydew;
    Canvas.SetLeft(excl, 150);
    Canvas.SetTop(excl, 320);
    excl.Click += btn_excl;
    cv.Children.Add(excl);
    esp.Height = 30;
    esp.Width = 30;
    esp.Content = " ";
    esp.FontSize = 20;
    esp.FontWeight = FontWeights.Bold;
    esp.Background = Brushes.Honeydew;
    Canvas.SetLeft(esp, 185);
    Canvas.SetTop(esp, 320);
    esp.Click += btn_esp;
    cv.Children.Add(esp);
    this.Content = cv;
}

private void btn_h(object sender, EventArgs ev)
{
    txtb.Text = txtb.Text + "h";
}

private void btn_e(object sender, EventArgs ev)
{
    txtb.Text = txtb.Text + "e";
}

private void btn_l(object sender, EventArgs ev)
{
    txtb.Text = txtb.Text + "l";
}

private void btn_o(object sender, EventArgs ev)
{
    txtb.Text = txtb.Text + "o";
}

private void btn_excl(object sender, EventArgs ev)
{
    txtb.Text = txtb.Text + "!";
}

private void btn_esp(object sender, EventArgs ev)
{
    txtb.Text = txtb.Text + " ";
}
```

{{% /expand %}}

---


### Exercice 2 : La Checkbox

{{% exercice %}}
Pour aller plus loin, vous pouvez essayer de reproduire ceci en dynamique :
{{% /exercice %}}

![image6](/img/3.2/img06.png?height=200px)

![image7](/img/3.2/img07.png?height=200px)

{{% expand "Correction" %}}

```csharp
Canvas cv = new Canvas();

TextBox t_fname = new TextBox();
TextBox t_lname = new TextBox();
TextBox t_birth = new TextBox();
TextBox t_mail = new TextBox();
TextBox t_tele = new TextBox();

Button sd = new Button();

ListBox result = new ListBox();

public MainWindow()
{
    InitializeComponent();
    MakingCanvas();
}

private void MakingCanvas()
{

    cv.Height = 500;
    cv.Width = 500;
    Label lb = new Label();
    lb.Height = 50;
    lb.Width = 400;
    lb.Foreground = Brushes.BlueViolet;
    lb.FontSize = 20;
    lb.HorizontalContentAlignment = HorizontalAlignment.Center;
    lb.FontWeight = FontWeights.Bold;
    lb.Content = "Press 'Enter' key, for delivering values";
    Canvas.SetLeft(lb, 10);
    Canvas.SetTop(lb, 20);
    cv.Children.Add(lb);
    Label fname = new Label();
    fname.Height = 30;
    fname.Width = 100;
    fname.FontSize = 15;
    fname.FontWeight = FontWeights.Bold;
    fname.Content = "First Name";
    Canvas.SetLeft(fname, 20);
    Canvas.SetTop(fname, 80);
    cv.Children.Add(fname);
    Label lname = new Label();
    lname.Height = 30;
    lname.Width = 100;
    lname.FontSize = 15;
    lname.FontWeight = FontWeights.Bold;
    lname.Content = "Last Name";
    Canvas.SetLeft(lname, 20);
    Canvas.SetTop(lname, 140);
    cv.Children.Add(lname);
    Label birth = new Label();
    birth.Height = 30;
    birth.Width = 200;
    birth.FontSize = 15;
    birth.FontWeight = FontWeights.Bold;
    birth.Content = "Birth (dd/mm/yyyy)";
    Canvas.SetLeft(birth, 20);
    Canvas.SetTop(birth, 200);
    cv.Children.Add(birth);
    Label tele = new Label();
    tele.Height = 30;
    tele.Width = 200;
    tele.FontSize = 15;
    tele.FontWeight = FontWeights.Bold;
    tele.Content = "Telephone";
    Canvas.SetLeft(tele, 20);
    Canvas.SetTop(tele, 260);
    cv.Children.Add(tele);
    Label mail = new Label();
    mail.Height = 30;
    mail.Width = 200;
    mail.FontSize = 15;
    mail.FontWeight = FontWeights.Bold;
    mail.Content = "E-MAIL";
    Canvas.SetLeft(mail, 20);
    Canvas.SetTop(mail, 320);
    cv.Children.Add(mail);
    t_fname.Height = 30;
    t_fname.Width = 100;
    t_fname.FontSize = 15;
    t_fname.VerticalContentAlignment = VerticalAlignment.Center;
    Canvas.SetLeft(t_fname, 22);
    Canvas.SetTop(t_fname, 110);
    cv.Children.Add(t_fname);
    t_lname.Height = 30;
    t_lname.Width = 100;
    t_lname.FontSize = 15;
    t_lname.VerticalContentAlignment = VerticalAlignment.Center;
    Canvas.SetLeft(t_lname, 22);
    Canvas.SetTop(t_lname, 170);
    cv.Children.Add(t_lname);
    t_birth.Height = 30;
    t_birth.Width = 100;
    t_birth.FontSize = 15;
    t_birth.VerticalContentAlignment = VerticalAlignment.Center;
    Canvas.SetLeft(t_birth, 22);
    Canvas.SetTop(t_birth, 230);
    cv.Children.Add(t_birth);
    t_tele.Height = 30;
    t_tele.Width = 100;
    t_tele.FontSize = 13;
    t_tele.VerticalContentAlignment = VerticalAlignment.Center;
    Canvas.SetLeft(t_tele, 22);
    Canvas.SetTop(t_tele, 290);
    cv.Children.Add(t_tele);
    t_mail.Height = 30;
    t_mail.Width = 100;
    t_mail.FontSize = 13;
    t_mail.VerticalContentAlignment = VerticalAlignment.Center;
    Canvas.SetLeft(t_mail, 22);
    Canvas.SetTop(t_mail, 350);
    cv.Children.Add(t_mail);
    Label youare = new Label();
    youare.Height = 50;
    youare.Width = 100;
    youare.FontSize = 20;
    youare.FontWeight = FontWeights.Bold;
    youare.Content = "You Are";
    youare.Foreground = Brushes.DodgerBlue;
    Canvas.SetLeft(youare, 300);
    Canvas.SetTop(youare, 100);
    cv.Children.Add(youare);
    result.Height = 200;
    result.Width = 200;
    result.FontSize = 12;
    result.FontWeight = FontWeights.SemiBold;
    Canvas.SetLeft(result, 240);
    Canvas.SetTop(result, 150);
    cv.Children.Add(result);
    sd.Height = 25;
    sd.Width = 50;
    sd.FontSize = 13;
    sd.Content = "Send";
    Canvas.SetLeft(sd, 45);
    Canvas.SetTop(sd, 400);
    cv.Children.Add(sd);
    t_fname.Focus();
    t_fname.KeyDown += T_fname_KeyDown;
    t_lname.KeyDown += T_lname_KeyDown;
    t_birth.KeyDown += T_birth_KeyDown;
    t_tele.KeyDown += T_tele_KeyDown;
    t_mail.KeyDown += T_mail_KeyDown;
    sd.Click += btn_send;
    this.Content = cv;
}

private void T_fname_KeyDown(object sender, KeyEventArgs e)
{
    if (e.Key.Equals(Key.Enter))
    {
        t_lname.Focus();
    }
    else if (e.Key.Equals(Key.Tab))
    {
        t_fname.Text = "Press Enter";
    }
}

private void T_lname_KeyDown(object sender, KeyEventArgs e)
{
    if (e.Key.Equals(Key.Enter))
    {
        t_birth.Focus();
    }
    else if (e.Key.Equals(Key.Tab))
    {
        t_lname.Text = "Press Enter";
    }
}

private void T_birth_KeyDown(object sender, KeyEventArgs e)
{
    if (e.Key.Equals(Key.Enter))
    {
        t_tele.Focus();
    }

    else if (e.Key.Equals(Key.Tab))
    {
        t_birth.Text = "Press Enter";
    }
}

private void T_tele_KeyDown(object sender, KeyEventArgs e)
{
    if (e.Key.Equals(Key.Enter))
    {
        t_mail.Focus();
    }
    else if (e.Key.Equals(Key.Tab))
    {
        t_tele.Text = "Press Enter";
    }
}

private void T_mail_KeyDown(object sender, KeyEventArgs e)
{
    if (e.Key.Equals(Key.Enter))
    {
        sd.Focus();
    }
    else if (e.Key.Equals(Key.Tab))
    {
        t_mail.Text = "Press Enter";
    }
}

private void btn_send(object sender, EventArgs e)
{
    result.Items.Add("Your first Name : " + t_fname.Text);
    result.Items.Add("Your Last Name : " + t_lname.Text);
    result.Items.Add("Your birth : " + t_birth.Text);
    result.Items.Add("Your Phone Number : " + t_tele.Text);
    result.Items.Add("Your E-MAIL Address : " + t_mail.Text);
    sd.IsEnabled = false;
}
```

{{% /expand %}}

---


### Exercice 3 : Le Stack Panel

{{% exercice %}}
Essayez d’obtenir grâce au Stack Panel le résultat suivant :
{{% /exercice %}}

![image8](/img/3.2/img08.png?height=200px)

![image9](/img/3.2/img09.png?height=200px)

{{% expand "Correction" %}}

```csharp
Grid myGrid = new Grid();

ListBox lbx = new ListBox();
TextBox txtb1 = new TextBox();
TextBox txtb2 = new TextBox();
TextBox txtb3 = new TextBox();

public MainWindow()
{
    InitializeComponent();
    MakingStackPanel();
}

private void MakingStackPanel()
{
    StackPanel sp = new StackPanel();
    sp.Orientation = Orientation.Vertical;
    sp.Width = 400;
    sp.Height = 500;
    sp.HorizontalAlignment = HorizontalAlignment.Left;
    sp.VerticalAlignment = VerticalAlignment.Top;
    sp.Background = Brushes.AliceBlue;
    Label lb = new Label();
    lb.Height = 50;
    lb.Width = 400;
    lb.Content = "Simple Message !";
    lb.FontSize = 25;
    lb.Foreground = Brushes.IndianRed;
    lb.HorizontalContentAlignment = HorizontalAlignment.Center;
    lb.FontWeight = FontWeights.Bold;
    sp.Children.Add(lb);
    txtb1.Width = 300;
    txtb1.Height = 50;
    txtb1.IsReadOnly = true;
    sp.Children.Add(txtb1);
    txtb2.Width = 300;
    txtb2.Height = 50;
    txtb2.IsReadOnly = true;
    sp.Children.Add(txtb2);
    txtb3.Width = 300;
    txtb3.Height = 50;
    txtb3.IsReadOnly = true;
    txtb3.Margin = new Thickness(0, 0, 0, 125);
    sp.Children.Add(txtb3);
    Button btn1 = new Button();
    btn1.Height = 45;
    btn1.Width = 300;
    btn1.FontSize = 15;
    btn1.Content = "Hi, I'm PIMO.";
    btn1.Click += btn_hi;
    sp.Children.Add(btn1);
    Button btn2 = new Button();
    btn2.Height = 45;
    btn2.Width = 300;
    btn2.FontSize = 15;
    btn2.Content = "How is the weather in Paris?";
    btn2.Click += btn_weather;
    sp.Children.Add(btn2);
    Button btn3 = new Button();
    btn3.Height = 45;
    btn3.Width = 300;
    btn3.FontSize = 15;
    btn3.Content = "I hope you be healthy !";
    btn3.Click += btn_healthy;
    this.Content = sp;
    sp.Children.Add(btn3);
}

private void btn_hi(object sender, EventArgs e)
{
    txtb1.Text = "Hi, I'm PIMO.";
}

private void btn_weather(object sender, EventArgs e)
{
    txtb2.Text = "How is the weather in Paris?";
}

private void btn_healthy(object sender, EventArgs e)
{
    txtb3.Text = "I hope you be healthy !";
}
```

{{% /expand %}}

---


### Exercice 4 : Le Canvas

{{% exercice %}}
Essayez d’obtenir grâce au Canvas et en dynamique le résultat suivant :
{{% /exercice %}}

![image12](/img/3.2/img12.png?height=200px)

{{% expand "Correction" %}}

```csharp
public MainWindow()
{
    InitializeComponent();
    Canvas cv = new Canvas();
    cv.Width = 1500;
    cv.Height = 1500;
    Rectangle r1 = new Rectangle();
    r1.Width = 500;
    r1.Height = 170;
    r1.Fill = Brushes.Red;
    Canvas.SetLeft(r1, 170);
    Canvas.SetTop(r1, 60);
    Rectangle r2 = new Rectangle();
    r2.Width = 700;
    r2.Height = 170;
    r2.Fill = Brushes.Red;
    Canvas.SetLeft(r2, 70);
    Canvas.SetTop(r2, 170);
    Rectangle r3 = new Rectangle();
    r3.Width = 150;
    r3.Height = 80;
    r3.Fill = Brushes.LightSkyBlue;
    Canvas.SetLeft(r3, 450);
    Canvas.SetTop(r3, 85);
    Rectangle r4 = new Rectangle();
    r4.Width = 150;
    r4.Height = 80;
    r4.Fill = Brushes.LightSkyBlue;
    Canvas.SetLeft(r4, 215);
    Canvas.SetTop(r4, 85);
    Ellipse e1 = new Ellipse();
    e1.Width = 150;
    e1.Height = 150;
    e1.Fill = Brushes.Black;
    Canvas.SetLeft(e1, 120);
    Canvas.SetTop(e1, 230);
    Ellipse e2 = new Ellipse();
    e2.Width = 150;
    e2.Height = 150;
    e2.Fill = Brushes.Black;
    Canvas.SetLeft(e2, 550);
    Canvas.SetTop(e2, 230);
    cv.Children.Add(r1);
    cv.Children.Add(r2);
    cv.Children.Add(r3);
    cv.Children.Add(r4);
    cv.Children.Add(e1);
    cv.Children.Add(e2);
    this.Content = cv;
}
```

{{% /expand %}}