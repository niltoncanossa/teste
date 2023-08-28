namespace semafaroImg
{

    public partial class semaforo : Form
    {
        public semaforo()
        {
            InitializeComponent();
        }

        private void btnLigar_Click(object sender, EventArgs e)
        {
            //Inicializa o contador assim que clicar no botão Ligar
            contador.Enabled = true;
        }

        // Cria uma variavel  Caso do tipo inteira com valor 0 para o switch case 
        int caso = 0;
        private void contador_Tick(object sender, EventArgs e)
        {
            /*
             * Programa: Semáforo
             * Versão 1.0
             * Autor: Tainan Rezende
             * Data: 24/08/2023
             * Descrição: 
             * - Programa de um semáforo que começa a funcionar após o usuário clicar em ligar
             * - Utiliza de switch case e imagens para poder representar as cores de um semáforo
             * - Utiliza um temporizador com valores diferentes para cada cor.
            */

            // Faz a escolha do caso, "ligando" e "desligando as imagens, setando o temporizador em 6 segundos
            // E em 4 segundos caso seja a cor amarela ligada.
            switch (caso)
            {
                case 0:
                    imgVerde.Image = Image.FromFile(@"C:\Users\nilton.cdiogo\source\repos\semafaroImg\img\cinza.png");
                    imgVermelho.Image = Image.FromFile(@"C:\Users\nilton.cdiogo\source\repos\semafaroImg\img\vermelho.png");
                    contador.Interval = 6000;
                    caso = 1;
                    break;
                case 1:
                    imgVermelho.Image = Image.FromFile(@"C:\Users\nilton.cdiogo\source\repos\semafaroImg\img\cinza.png");
                    imgAmarelo.Image = Image.FromFile(@"C:\Users\nilton.cdiogo\source\repos\semafaroImg\img\amarelo.png");
                    contador.Interval = 4000;
                    caso = 2;
                    break;
                case 2:
                    imgAmarelo.Image = Image.FromFile(@"C:\Users\nilton.cdiogo\source\repos\semafaroImg\img\cinza.png");
                    imgVerde.Image = Image.FromFile(@"C:\Users\nilton.cdiogo\source\repos\semafaroImg\img\verde.png");
                    contador.Interval = 5000;
                    caso = 0;
                    break;
            }
        }

        private void btnDesligar_Click(object sender, EventArgs e)
        {
            // Seta todos as luzes como cinza (desligado), volta a variavel "caso" para 0
            // Coloca o intervalo do contador em 1 para que o desligamento seja mais rápido
            // Desliga o contador.
            imgVermelho.Image = Image.FromFile(@"C:\Users\nilton.cdiogo\source\repos\semafaroImg\img\cinza.png");
            imgAmarelo.Image = Image.FromFile(@"C:\Users\nilton.cdiogo\source\repos\semafaroImg\img\cinza.png");
            imgVerde.Image = Image.FromFile(@"C:\Users\nilton.cdiogo\source\repos\semafaroImg\img\cinza.png");
            caso = 0;
            contador.Interval = 1;
            contador.Enabled = false;

        }

        private void btnSair_Click(object sender, EventArgs e)
        {
            // Abre uma caixa de mensagem perguntando se o usuário realmente quer sair do programa, caso sim, fecha o programa
            DialogResult dialogo = MessageBox.Show("Realmente deseja sair?", "Saindo do programa!", MessageBoxButtons.YesNo);
            if (dialogo == DialogResult.Yes)
            {
                Application.Exit();
            }
        }
    }
}

