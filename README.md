
import io.restassured.path.json.JsonPath;
import io.restassured.response.Response;
import static io.restassured.RestAssured.given;
import static org.junit.Assert.assertTrue;

import java.util.Arrays;
import java.util.List;

public class NewClass {
    public static void main(String[] args) {
        List<String> isbnIds = Arrays.asList("9781449325862", "9781449331818","9781449337711","9781449365035","9781491904244","9781491950296","9781593275846","9781593277574");

        for (String isbnId : isbnIds) {
            String url = "https://bookstore.toolsqa.com/BookStore/v1/Books?isbn=" + isbnId;
            Response response = given()
                    .when()
                    .get(url);

            JsonPath jsonPath = response.jsonPath();

            // Validate data type of "isbn" field
            String isbn = jsonPath.get("isbn");
            if (isbn == null) {
                continue;
            }
            assertTrue(isbn.getClass().equals(String.class));

            // Validate data type of "title" field
            String title = jsonPath.get("title");
            assertTrue(title.getClass().equals(String.class));

            // Validate data type of "subTitle" field
            String subTitle = jsonPath.get("subTitle");
            assertTrue(subTitle.getClass().equals(String.class));

            // Validate data type of "author" field
            String author = jsonPath.get("author");
            assertTrue(author.getClass().equals(String.class));

            // Validate data type of "publish_date" field
            String publishDate = jsonPath.get("publish_date");
            assertTrue(publishDate.getClass().equals(String.class));

            // Validate data type of "publisher" field
            String publisher = jsonPath.get("publisher");
            assertTrue(publisher.getClass().equals(String.class));

            // Validate data type of "pages" field
            int pages = jsonPath.get("pages");
            assertTrue(Integer.class.isInstance(pages));

            // Validate data type of "description" field
            String description = jsonPath.get("description");
            assertTrue(description.getClass().equals(String.class));

            // Validate data type of "Website" field
            String website = jsonPath.get("Website");
            assertTrue(website.getClass().equals(String.class));
            
            
        }
    }
}
