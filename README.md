# Leetcode---435
Non-Overlapping Intervals
// code in java
import java.util.Arrays;

public class Solution {
    public int eraseOverlapIntervals(int[][] intervals) {
        if (intervals.length == 0) return 0;

        // Sort intervals by end time
        Arrays.sort(intervals, (a, b) -> a[1] - b[1]);

        int count = 0;
        int end = intervals[0][1];

        for (int i = 1; i < intervals.length; i++) {
            if (intervals[i][0] < end) {
                count++;
            } else {
                end = intervals[i][1];
            }
        }

        return count;
    }

    public static void main(String[] args) {
        Solution solution = new Solution();
        int[][] intervals = {{1, 2}, {2, 3}, {3, 4}, {1, 3}};
        int result = solution.eraseOverlapIntervals(intervals);
        System.out.println(result); // Output: 1
    }
}
