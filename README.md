# tensorflow-mobilenet-android
Using Tensorflow, retrain sample dataset with mobilenet model. Later will be used on Android App.

<b>Steps to retrain a sample dataset</b>

1. Run following command on CMD prompt to retrain 

python retrain.py --image_dir "<DatasetPath>" --bottleneck_dir="<Bottleneck Dir Path>"
--output_graph="retrained_graph.pb"
--output_labels="retrained_labels.txt"
--tfhub_module https://tfhub.dev/google/imagenet/mobilenet_v2_100_224/feature_vector/1

2. Run Following Command on CMD Prompt, To test retrained model

python label_image.py 
--graph="retrained_graph.pb"
--labels="retrained_labels.txt"
--input_layer=Placeholder --output_layer=final_result
--image="<Sample Image path From DataSet>"
--input_height=224 --input_width=224

3. Paste retrained files namely retraned_graph.pb and retrained_labels.txt into asset folder of 
    tensorflow android lite: tensorflow\tensorflow\examples\android
    
 4. Update following lines in ClassiferActivity.java,
 
    private static final String MODEL_FILE = "file:///android_asset/retrained_graph.pb";
    private static final String LABEL_FILE =   "file:///android_asset/retrained_labels.txt";

5. build & Run Android App.. 
6. Test imageclassification on the dataset which is trained.
   Ex: Mouse, Focus your camera on mouse .. 
