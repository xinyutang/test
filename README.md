import java.util.*;

public class TopKHotelsFinder {
    public static List<Integer> awardTopKHotels(String positiveKeywords, String negativeKeywords,
                                                List<Integer> hotelIds, List<String> reviews, int k) {
        Set<String> positiveWords = new HashSet<>(Arrays.asList(positiveKeywords.split(" ")));
        Set<String> negativeWords = new HashSet<>(Arrays.asList(negativeKeywords.split(" ")));

        Map<Integer, Integer> hotelScores = new HashMap<>();
        for (int i = 0; i < reviews.size(); i++) {
            int hotelId = hotelIds.get(i);
            int score = hotelScores.getOrDefault(hotelId, 0);
            String[] words = reviews.get(i).split(" ");

            int positiveCount = 0, negativeCount = 0;
            for (String word : words) {
                word = word.replaceAll("[.,]", "");
                if (positiveWords.contains(word.toLowerCase())) {
                    positiveCount++;
                }
                if (negativeWords.contains(word.toLowerCase())) {
                    negativeCount++;
                }
            }
            int updatedScore = score + 3 * positiveCount - negativeCount;
            hotelScores.put(hotelId, updatedScore);
        }

        PriorityQueue<Map.Entry<Integer, Integer>> pq = new PriorityQueue<>(
                Comparator.comparingInt(Map.Entry::getValue).thenComparing(Map.Entry::getKey)
        );

        for (Map.Entry<Integer, Integer> entry : hotelScores.entrySet()) {
            pq.offer(entry);
            if (pq.size() > k) {
                pq.poll();
            }
        }

        List<Integer> result = new ArrayList<>();
        while (!pq.isEmpty()) {
            result.add(0, pq.poll().getKey());
        }

        return result;
    }
}
