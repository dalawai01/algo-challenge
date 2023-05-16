import java.lang.Math;

public class Main {
    public static void main(String[] args) {
        double jenna_distance = distance_covered(12, 5, 16, 1234);
        System.out.println(jenna_distance);
    }

    public static double distance_covered(int speed, int run_time, int rest_time, int total_time) {
        double distance = 0;
        while (total_time > 0) {
            if (total_time >= run_time) {
                distance += speed * run_time;
                total_time -= run_time;
            } else {
                distance += speed * total_time;
                total_time = 0;
            }
            total_time -= rest_time;
        }
        return distance;
    }
}

## Output

3540.0

![Challenge-2](https://github.com/dalawai01/algo-challenge/assets/130344323/0541b431-ab8e-471a-88c6-0ad343750f5a)

