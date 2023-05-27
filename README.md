# shiny-lamp
Cloud Based Service
import javax.swing.*;

import java.awt.*;

public class ShinyLamp {

    public static void main(String[] args) {

        JFrame frame = new JFrame("Shiny Lamp");

        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        frame.setSize(500, 500);

        

        BallPanel ballPanel = new BallPanel();

        frame.add(ballPanel);

        

        frame.setVisible(true);

        

        // Start the animation

        ballPanel.startAnimation();

    }

}

class BallPanel extends JPanel {

    private int x = 0;

    private int y = 0;

    private int xSpeed = 1;

    private int ySpeed = 1;

    

    private static final int PANEL_WIDTH = 500;

    private static final int PANEL_HEIGHT = 500;

    private static final int BALL_SIZE = 50;

    

    public void startAnimation() {

        while (true) {

            updateBallPosition();

            repaint();

            

            try {

                Thread.sleep(10);

            } catch (InterruptedException e) {

                e.printStackTrace();

            }

        }

    }

    

    private void updateBallPosition() {

        if (x + xSpeed < 0 || x + BALL_SIZE + xSpeed > PANEL_WIDTH) {

            xSpeed = -xSpeed;

        }

        

        if (y + ySpeed < 0 || y + BALL_SIZE + ySpeed > PANEL_HEIGHT) {

            ySpeed = -ySpeed;

        }

        

        x += xSpeed;

        y += ySpeed;

    }

    

    @Override

    protected void paintComponent(Graphics g) {

        super.paintComponent(g);

        

        g.setColor(Color.RED);

        g.fillOval(x, y, BALL_SIZE, BALL_SIZE);

    }

}

