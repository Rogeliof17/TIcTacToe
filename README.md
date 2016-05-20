# TIcTacToe
/**
 * Created by Rogelio on 5/16/2016.
 */
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
public class TicTacToe implements ActionListener
{

    JFrame PlayArea = new JFrame("Tic-Tac-Toe");

    private final int WINDOW_WIDTH = 400;       //width of frame
    private final int WINDOW_HEIGHT = 400;      //height of frame
    private int turn = 0;                       //to keep track of turns
    private String letter = "";                 //default image on buttons

    //buttons
    JButton a1 = new JButton("");
    JButton a2 = new JButton("");
    JButton a3 = new JButton("");
    JButton b1 = new JButton("");
    JButton b2 = new JButton("");
    JButton b3 = new JButton("");
    JButton c1 = new JButton("");
    JButton c2 = new JButton("");
    JButton c3 = new JButton("");

    private boolean winner = false;

    //what the layout looks like
    /**      1  2   3
     *      ------------
     *    a |  |  |  |
     *      ------------
     *    b |  |  |  |
     *      ------------
     *    c |  |  |  |
    */
    public TicTacToe()
    {
        PlayArea.setTitle("Tic Tac Toe");                           //title on frame

        PlayArea.setSize(WINDOW_WIDTH, WINDOW_HEIGHT);              //size of frame

        PlayArea.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);    //action of close button

        PlayArea.setLayout(new GridLayout(3, 3));                   //3x3 grid layout

        //add the buttons to the play area
        PlayArea.add(a1);
        PlayArea.add(a2);
        PlayArea.add(a3);
        PlayArea.add(b1);
        PlayArea.add(b2);
        PlayArea.add(b3);
        PlayArea.add(c1);
        PlayArea.add(c2);
        PlayArea.add(c3);

        //connect the buttons to an action listener
        a1.addActionListener(this);
        a2.addActionListener(this);
        a3.addActionListener(this);
        b1.addActionListener(this);
        b2.addActionListener(this);
        b3.addActionListener(this);
        c1.addActionListener(this);
        c2.addActionListener(this);
        c3.addActionListener(this);

        //make grid visible
        PlayArea.setVisible(true);
    }//closes Tic-Tac-Toe method

    public void actionPerformed(ActionEvent push)
    {
        turn++;

        if (turn == 1 || turn == 3 || turn == 5
                || turn == 7 || turn == 9)
            letter = "X";

        else if (turn == 2 || turn == 4 || turn == 6
                || turn == 8)
            letter = "O";

        if(push.getSource() == a1)
        {
            a1.setText(letter);
            a1.setEnabled(false);

        }//close a1 push

        if(push.getSource() == a2)
        {
            a2.setText(letter);
            a2.setEnabled(false);

        }//close a2 push

        if(push.getSource() == a3)
        {
            a3.setText(letter);
            a3.setEnabled(false);

        }//close a2 push

        if(push.getSource() == b1)
        {
            b1.setText(letter);
            b1.setEnabled(false);

        }//close b1 push

        if(push.getSource() == b2)
        {
            b2.setText(letter);
            b2.setEnabled(false);

        }//close b2 push

        if(push.getSource() == b3)
        {
            b3.setText(letter);
            b3.setEnabled(false);

        }//close b3 push

        if(push.getSource() == c1)
        {
            c1.setText(letter);
            c1.setEnabled(false);

        }//close c1 push

        if(push.getSource() == c2)
        {
            c2.setText(letter);
            c2.setEnabled(false);

        }//close c2 push

        if(push.getSource() == c3)
        {
            c3.setText(letter);
            c3.setEnabled(false);

        }//close c3 push

        //column wins
        //leftmost column
        if (a1.getText() == b1.getText() && b1.getText()== c1.getText() && a1.getText() != "" )
        {winner = true;}

        //middle column
        else if (a2.getText() == b2.getText() && b2.getText()== c2.getText() && a2.getText() != "" )
        {winner = true;}
        //right most column
        else if (a3.getText() == b3.getText() && b3.getText()== c3.getText() && a3.getText() != "" )
        {winner = true;}

        //row wins
        //top row
        else if (a1.getText() == a2.getText() && a2.getText()== a3.getText() && a1.getText() != "")
        {winner = true;}

        //middle row
        else if (b1.getText() == b2.getText() && b2.getText()== b3.getText() && b1.getText() != "" )
        {winner = true;}

        //bottom row
        else if (c1.getText() == c2.getText() && c2.getText()== c3.getText() && c1.getText()!= "")
        {winner = true;}

        //cross wins
        //from top to bottom
        else if (a1.getText() == b2.getText() && b2.getText() == c3.getText() && a1.getText() != "")
        {winner = true;}

        //from bottom to top
        else if (a3.getText() == b2.getText() && b2.getText() == c1.getText() && a3.getText() != "")
        {winner = true;}

        //no winner
        else
            winner = false;

        //declare outcome
        if (winner == true)
        {JOptionPane.showMessageDialog(null, "The winner is "+ letter + "!!");}
        else if (turn == 9 && winner == false)
        {JOptionPane.showMessageDialog(null, "The game is tied.");}
    }//closes actionPerformed method



    //main
    public static void main(String[] args)
    {
     new TicTacToe();


    }//closes main
}//closes TicTacToe class
