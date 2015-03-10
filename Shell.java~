import javax.swing.*;
import java.awt.Color;
import java.awt.event.*;

import java.io.BufferedReader;
import java.io.InputStream;
import java.io.InputStreamReader;

public class Shell extends JFrame{
	
	//elementos gráficos
	JTextField tComando;
	JButton bEjecutar;
	JTextArea tResultado;
	JScrollPane sPane;
	JLabel shellcomandos;
	ImageIcon icono;

	//oyente de click de botón
	ActionListener alEjecutar;

	public Shell(){
		setSize(700,600);
		setTitle("SHELL"+System.getProperty("os.name"));
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
	}

	private void graficos(){
		getContentPane().setLayout(null);
		//cuadro de texto
		tComando = new JTextField();
		tComando.setBounds(50,50,250,30);
		add(tComando);
		icono=new ImageIcon("iconshell.png");		
		//botón para ejecutar comando
		bEjecutar = new JButton();
		bEjecutar.setBounds(400,20,100,98);
		bEjecutar.setIcon(icono);
		add(bEjecutar);
		bEjecutar.addActionListener(alEjecutar);
		//area de informacion
		shellcomandos = new JLabel("INGRESE COMANDO :");
		shellcomandos.setBounds(50,20,250,30);
		add(shellcomandos);
		//área de texto
		tResultado = new JTextArea();
		tResultado.setBounds(50,130,600,370);
		tResultado.setBackground(Color.BLACK);
		tResultado.setForeground(Color.GREEN);
		tResultado.setEditable(false);
		//scroll pane
		sPane = new JScrollPane(tResultado);
		sPane.setBounds(50,120,500,400);
		add(sPane);
		//
		setVisible(true);
	}

	private void acciones(){
		alEjecutar = new ActionListener(){
			public void actionPerformed(ActionEvent e){
				ejecutar();
			}
		};
	}

	private void ejecutar(){

		Process proc; 
		InputStream is_in;
		String s_aux;
		BufferedReader br;

		try
		{  try{ 	
			proc = Runtime.getRuntime().exec(tComando.getText());
		      }
		   catch(Exception e)
			{
			proc = Runtime.getRuntime().exec("cmd/c"+tComando.getText());				
			}
			is_in=proc.getInputStream();
			br=new BufferedReader (new InputStreamReader (is_in));
			s_aux = br.readLine();
            while (s_aux!=null)
            {	if((tComando.getText().equals("clear"))||(tComando.getText().equals("cls")))
		{tResultado.setText("");
		}
		else
            	tResultado.setText(tResultado.getText()+s_aux+"\n");
                s_aux = br.readLine();			
            } 
		}
		catch(Exception e)
		{
			e.getMessage();
		}


	}

	public static void main(String args[]){
		Shell ventana = new Shell();
		ventana.acciones();	
		ventana.graficos();	
	}

}
