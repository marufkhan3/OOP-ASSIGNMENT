import javax.swing.*;
import java.awt.*;
import java.awt.font.FontRenderContext;
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;
public class WordShape {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
// Step 1: Input the main name from the user
        System.out.println("Enter the main name :");
        String mainName = scanner.nextLine();
// Step 2: Input the inner names from the user
        System.out.println("Enter names to fill the text shape (type 'done' to finish):");
        List<String> innerNamesList = new ArrayList<>();
        while (true) {
            String name = scanner.nextLine();
            if (name.equalsIgnoreCase("done")) break;
            innerNamesList.add(name);
        }
        if (innerNamesList.isEmpty()) {
            System.out.println("No names entered. Exiting...");
            return;
        }
// Convert list to array
        String[] innerNames = innerNamesList.toArray(new String[0]);
// Step 3: Create GUI and render the main name
        JFrame frame = new JFrame("Names That Forming Main Name");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(800, 600);
        frame.add(new NamePanel(mainName, innerNames));
        frame.setVisible(true);
    }
}
class NamePanel extends JPanel {
    private final String mainName; // The main name shape (e.g., "MARUF")
    private final String[] innerNames; // Smaller names to fill the shape
    private int nameIndex = 0; // Current index of the inner name
    public NamePanel(String mainName, String[] innerNames) {
        this.mainName = mainName;
        this.innerNames = innerNames;
    }
    @Override
    protected void paintComponent(Graphics g) {
        super.paintComponent(g);
        Graphics2D g2d = (Graphics2D) g;
// Enable anti-aliasing for smooth text rendering
        g2d.setRenderingHint(RenderingHints.KEY_ANTIALIASING, RenderingHints.VALUE_ANTIALIAS_ON);
// Set up the font for the main name
        Font mainFont = new Font("Serif", Font.BOLD, 200);
        g2d.setFont(mainFont);
        FontMetrics fm = g2d.getFontMetrics(mainFont);
// Calculate position to center the main name
        int mainNameWidth = fm.stringWidth(mainName);
        int xCenter = (getWidth() - mainNameWidth) / 2;
        int yCenter = getHeight() / 2;
// Create a shape for the main name
        FontRenderContext frc = g2d.getFontRenderContext();
        Shape mainNameShape = mainFont.createGlyphVector(frc, mainName).getOutline(xCenter, yCenter);
// Set color for the main name (white)
        g2d.setColor(Color.WHITE);
// Fill the main name shape with white
        g2d.fill(mainNameShape);
// Set color for the inner names (blue)
        g2d.setColor(Color.BLUE);
// Grid size controls how fine the filling is (more granularity)
        int gridSize = 15;
// Iterate through the entire panel area
        for (int x = 0; x < getWidth(); x += gridSize) {
            for (int y = 0; y < getHeight(); y += gridSize) {
// Check if the current point (x, y) is inside the main name shape
                if (mainNameShape.contains(x, y)) {
// Draw the current inner name at this position
                    String currentName = innerNames[nameIndex];
                    g2d.setFont(new Font("SansSerif", Font.PLAIN, 10)); // Smaller font size for inner names
                    g2d.drawString(currentName, x, y);
// Move to the next inner name
                    nameIndex = (nameIndex + 1) % innerNames.length;
                }
            }
        }
// Optionally, you can also draw the outline of the main name for reference
        g2d.setColor(Color.LIGHT_GRAY);
        g2d.draw(mainNameShape);
    }
}




