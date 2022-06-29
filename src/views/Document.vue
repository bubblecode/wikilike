<script lang="tsx">
/* eslint-disable @typescript-eslint/no-explicit-any */
import { Vue } from "vue-class-component";
import { reactive, ref } from "vue";
import { useRoute, useRouter } from "vue-router";
import MdEditor from "md-editor-v3";
import {
  DocumentAdd,
  Delete,
  UploadFilled,
  ArrowRight,
  Unlock,
  Lock,
} from "@element-plus/icons-vue";
import "md-editor-v3/lib/style.css";

export default class Document extends Vue {
  route: any;
  router: any;
  md: { text: string };
  isEdit: boolean;
  mdEditor: any;
  constructor(props: any) {
    super(props);
    this.route = useRoute();
    this.router = useRouter();
    this.isEdit = false;
    this.mdEditor = ref();
    this.md = reactive({
      text: "### test",
    });
  }

  onDocAdd() {
    console.log("add document");
  }

  onDocEdit() {
    this.isEdit = true;
    console.log("编辑");
  }

  onDocEditClose() {
    this.isEdit = false;
    console.log("退出编辑");
  }

  onDocSave() {
    console.log("保存");
  }

  onDocDelete() {
    console.log("删除文档");
  }

  render() {
    return (
      <div class="document-main">
        <div class="document-breadcrumb">
          <el-breadcrumb separatorIcon={ArrowRight}>
            <el-breadcrumb-item to="{ path: '/' }">document</el-breadcrumb-item>
            <el-breadcrumb-item>{this.route.params.did}</el-breadcrumb-item>
          </el-breadcrumb>
        </div>
        <div class="toolbar">
          <el-tooltip content="添加" effect="light" placement="top">
            <el-button text bg icon={DocumentAdd} onClick={this.onDocAdd} />
          </el-tooltip>
          {!this.isEdit ? (
            <el-tooltip content="编辑" effect="light" placement="top">
              <el-button text bg icon={Lock} onClick={this.onDocEdit} />
            </el-tooltip>
          ) : (
            <>
              <el-tooltip content="退出编辑" effect="light" placement="top">
                <el-button text bg icon={Unlock} onClick={this.onDocEditClose} />
              </el-tooltip>
              <el-tooltip content="保存" effect="light" placement="top">
                <el-button text bg icon={UploadFilled} onClick={this.onDocSave} />
              </el-tooltip>
            </>
          )}
          <el-tooltip content="删除" effect="light" placement="top">
            <el-button text bg icon={Delete} onClick={this.onDocDelete} />
          </el-tooltip>
        </div>
        {this.isEdit ? (
          <MdEditor
            modelValue={this.md.text}
            previewOnly={false}
            onChange={(value) => (this.md.text = value)}
          />
        ) : (
          <div style={{ height: '100%' }}>
            <MdEditor
              modelValue={this.md.text}
              previewOnly={true}
              onChange={(value) => (this.md.text = value)}
            />
          </div>
        )}
      </div>
    );
  }
}
</script>

<style scoped>
.toolbar {
  background-color: #f5f7fa;
}
.document-breadcrumb {
  padding: 15px;
}
#md-editor-v3 {
  height: 800px;
  padding: 0px 10px 0px 10px;
}
</style>